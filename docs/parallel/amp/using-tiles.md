---
title: Usar mosaicos
ms.date: 11/19/2018
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
ms.openlocfilehash: ede62c80a83b5f5fc1d691bf52dde67140e68246
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405380"
---
# <a name="using-tiles"></a>Usar mosaicos

Puede utilizar la disposición en mosaico para maximizar la aceleración de la aplicación. Mosaico divide los subprocesos en subconjuntos rectangulares iguales o *iconos*. Si usa un tamaño apropiado del mosaico y el algoritmo de teselado, puede obtener mayor aceleración desde el código de C++ AMP. Los componentes básicos de disposición en mosaico son:

- `tile_static` variables. La principal ventaja del mosaico es la mejora de rendimiento de `tile_static` acceso. Acceso a datos en `tile_static` memoria puede ser mucho más rápida que el acceso a datos en el espacio global (`array` o `array_view` objetos). Se crea una instancia de la variable `tile_static` para cada mosaico y todos los subprocesos del mosaico tienen acceso a la variable. En un algoritmo en mosaico típico, los datos se copian en `tile_static` memoria una vez de la memoria global y, a continuación, obtener acceso a muchas veces desde el `tile_static` memoria.

- [tile_barrier:: Wait (método)](reference/tile-barrier-class.md#wait). Una llamada a `tile_barrier::wait` suspende la ejecución del subproceso actual hasta que todos los subprocesos en el mismo mosaico llaman a `tile_barrier::wait`. No puede garantizar el orden en que los subprocesos se ejecutarán en, solo que no hay subprocesos del mosaico se ejecutará más allá de la llamada a `tile_barrier::wait` hasta que todos los subprocesos hayan alcanzado la llamada. Esto significa que mediante la `tile_barrier::wait` método, puede realizar tareas en un mosaico a mosaico en lugar de un subproceso por subproceso. Un algoritmo de disposición en mosaico típico tiene código para inicializar el `tile_static` memoria para todo el mosaico seguido por una llamada a `tile_barrer::wait`. Código que sigue `tile_barrier::wait` contiene los cálculos que requieren acceso a todos los `tile_static` valores.

- Indización local y global. Tener acceso al índice del subproceso que concierne a toda la `array_view` o `array` objeto y el índice que concierne al mosaico. Utiliza el índice local puede hacer más fácil leerlos y depurar su código. Normalmente, se utiliza la indización local para tener acceso a `tile_static` variables y la indización global para tener acceso a `array` y `array_view` variables.

- [tiled_extent (clase)](../../parallel/amp/reference/tiled-extent-class.md) y [tiled_index (clase)](../../parallel/amp/reference/tiled-index-class.md). Usa un `tiled_extent` en lugar del objeto un `extent` objeto en el `parallel_for_each` llamar a. Usa un `tiled_index` en lugar del objeto un `index` objeto en el `parallel_for_each` llamar a.

Para aprovechar las ventajas del mosaico, el algoritmo debe dividir el dominio del cálculo en mosaicos y, a continuación, copie los datos de mosaico en `tile_static` variables para un acceso más rápido.

## <a name="example-of-global-tile-and-local-indices"></a>Ejemplo de Global, icono y los índices locales

El siguiente diagrama representa una matriz de 8 x 9 de datos que se organizan en mosaicos de 2 x 3.

![8&#45;por&#45;matriz 9 dividido en 2&#45;por&#45;3 iconos](../../parallel/amp/media/usingtilesmatrix.png "8&#45;por&#45;matriz 9 dividido en 2&#45;por&#45;3 iconos")

En el ejemplo siguiente se muestra el icono global, y los índices locales de esta matriz en mosaico. Un `array_view` objeto se crea mediante el uso de los elementos de tipo `Description`. El `Description` contiene la información global, icono y los índices locales del elemento de la matriz. El código en la llamada a `parallel_for_each` establece los valores de la información global, icono y los índices locales de cada elemento. La salida muestra los valores en el `Description` estructuras.

```cpp
#include <iostream>
#include <iomanip>
#include <Windows.h>
#include <amp.h>
using namespace concurrency;

const int ROWS = 8;
const int COLS = 9;

// tileRow and tileColumn specify the tile that each thread is in.
// globalRow and globalColumn specify the location of the thread in the array_view.
// localRow and localColumn specify the location of the thread relative to the tile.
struct Description {
    int value;
    int tileRow;
    int tileColumn;
    int globalRow;
    int globalColumn;
    int localRow;
    int localColumn;
};

// A helper function for formatting the output.
void SetConsoleColor(int color) {
    int colorValue = (color == 0)  4 : 2;
    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), colorValue);
}

// A helper function for formatting the output.
void SetConsoleSize(int height, int width) {
    COORD coord;

    coord.X = width;
    coord.Y = height;
    SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), coord);

    SMALL_RECT* rect = new SMALL_RECT();
    rect->Left = 0;
    rect->Top = 0;
    rect->Right = width;
    rect->Bottom = height;
    SetConsoleWindowInfo(GetStdHandle(STD_OUTPUT_HANDLE), true, rect);
}

// This method creates an 8x9 matrix of Description structures.
// In the call to parallel_for_each, the structure is updated
// with tile, global, and local indices.
void TilingDescription() {
    // Create 72 (8x9) Description structures.
    std::vector<Description> descs;
    for (int i = 0; i < ROWS * COLS; i++) {
        Description d = {i, 0, 0, 0, 0, 0, 0};
        descs.push_back(d);
    }

    // Create an array_view from the Description structures.
    extent<2> matrix(ROWS, COLS);
    array_view<Description, 2> descriptions(matrix, descs);

    // Update each Description with the tile, global, and local indices.
    parallel_for_each(descriptions.extent.tile< 2, 3>(),
        [=] (tiled_index< 2, 3> t_idx) restrict(amp)
    {
        descriptions[t_idx].globalRow = t_idx.global[0];
        descriptions[t_idx].globalColumn = t_idx.global[1];
        descriptions[t_idx].tileRow = t_idx.tile[0];
        descriptions[t_idx].tileColumn = t_idx.tile[1];
        descriptions[t_idx].localRow = t_idx.local[0];
        descriptions[t_idx].localColumn= t_idx.local[1];
    });

    // Print out the Description structure for each element in the matrix.
    // Tiles are displayed in red and green to distinguish them from each other.
    SetConsoleSize(100, 150);
    for (int row = 0; row < ROWS; row++) {
        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Value: " << std::setw(2) << descriptions(row, column).value << "      ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Tile:   " << "(" << descriptions(row, column).tileRow << "," << descriptions(row, column).tileColumn << ")  ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Global: " << "(" << descriptions(row, column).globalRow << "," << descriptions(row, column).globalColumn << ")  ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Local:  " << "(" << descriptions(row, column).localRow << "," << descriptions(row, column).localColumn << ")  ";
        }
        std::cout << "\n";
        std::cout << "\n";
    }
}

void main() {
    TilingDescription();
    char wait;
    std::cin >> wait;
}
```

El trabajo principal del ejemplo está en la definición de la `array_view` objeto y la llamada a `parallel_for_each`.

1. El vector de `Description` estructuras se copia en un 8 x 9 `array_view` objeto.

2. El `parallel_for_each` se llama al método con un `tiled_extent` objeto como el dominio del cálculo. El `tiled_extent` objeto se crea mediante una llamada a la `extent::tile()` método de la `descriptions` variable. Los parámetros de tipo de la llamada a `extent::tile()`, `<2,3>`, especifique que se crean mosaicos de 2 x 3. Por lo tanto, la matriz de 8 x 9 está dispuesta en 12 mosaicos, cuatro filas y tres columnas.

3. El `parallel_for_each` se llama al método mediante el uso de un `tiled_index<2,3>` objeto (`t_idx`) como el índice. Los parámetros de tipo del índice (`t_idx`) debe coincidir con los parámetros de tipo del dominio de proceso (`descriptions.extent.tile< 2, 3>()`).

4. Cuando se ejecuta cada subproceso, el índice `t_idx` devuelve información acerca de qué icono el subproceso está en (`tiled_index::tile` propiedad) y la ubicación del subproceso dentro del mosaico (`tiled_index::local` propiedad).

## <a name="tile-synchronizationtilestatic-and-tilebarrierwait"></a>Sincronización del mosaico: tile_static y tile_barrier:: wait

El ejemplo anterior muestra el diseño de mosaico y los índices, pero no es en sí mismo muy útil.  Mosaico resulta útil cuando los mosaicos son enteros para el algoritmo y explotan `tile_static` variables. Dado que todos los subprocesos de un mosaico tienen acceso a `tile_static` variables, llamadas a `tile_barrier::wait` se usan para sincronizar el acceso a la `tile_static` variables. Aunque todos los subprocesos de un mosaico tienen acceso a la `tile_static` variables, no hay ningún orden garantizado de la ejecución de subprocesos del mosaico. El ejemplo siguiente muestra cómo usar `tile_static` variables y `tile_barrier::wait` método para calcular el valor medio de cada mosaico. Estas son las claves para entender el ejemplo:

1. Los datos sin formato se almacenan en una matriz de 8 x 8.

2. El tamaño del mosaico es de 2 x 2. Esto crea una cuadrícula 4 x 4 de iconos y los promedios se pueden almacenar en una matriz de 4 x 4 mediante el uso de un `array` objeto. Hay solo un número limitado de tipos que se pueden capturar por referencia en una función con restricción AMP. La `array` clase es uno de ellos.

3. El tamaño de matriz y el tamaño de muestra se definen mediante `#define` instrucciones, ya que los parámetros de tipo para `array`, `array_view`, `extent`, y `tiled_index` deben ser valores constantes. También puede usar `const int static` declaraciones. Como ventaja adicional, es muy fácil cambiar el tamaño de muestra para calcular el promedio mosaicos 4 x 4.

4. Un `tile_static` es declarar una matriz de 2 x 2 de valores flotantes para cada mosaico. Aunque la declaración está en la ruta de acceso de código para cada subproceso, se crea solo una matriz para cada mosaico en la matriz.

5. Hay una línea de código para copiar los valores de cada mosaico a la `tile_static` matriz. Para cada subproceso, después de que el valor se copia en la matriz, la ejecución en el subproceso se detenga debido a la llamada a `tile_barrier::wait`.

6. Cuando todos los subprocesos de un mosaico han alcanzado la barrera, se puede calcular el promedio. Dado que el código se ejecuta para cada subproceso, hay un `if` instrucción para calcular solo el promedio en un subproceso. El promedio se almacena en la variable de promedios. La barrera es esencialmente el concepto que controla los cálculos por mosaico, tanto como se usarían un `for` bucle.

7. Los datos en el `averages` variable porque es un `array` de objetos, se deben copiar al host. Este ejemplo utiliza el operador de conversión de vectores.

8. En el ejemplo completo, puede cambiar SAMPLESIZE a 4 y el código se ejecuta correctamente sin realizar ningún otro cambio.

```cpp
#include <iostream>
#include <amp.h>
using namespace concurrency;

#define SAMPLESIZE 2
#define MATRIXSIZE 8
void SamplingExample() {

    // Create data and array_view for the matrix.
    std::vector<float> rawData;
    for (int i = 0; i < MATRIXSIZE * MATRIXSIZE; i++) {
        rawData.push_back((float)i);
    }
    extent<2> dataExtent(MATRIXSIZE, MATRIXSIZE);
    array_view<float, 2> matrix(dataExtent, rawData);

    // Create the array for the averages.
    // There is one element in the output for each tile in the data.
    std::vector<float> outputData;
    int outputSize = MATRIXSIZE / SAMPLESIZE;
    for (int j = 0; j < outputSize * outputSize; j++) {
        outputData.push_back((float)0);
    }
    extent<2> outputExtent(MATRIXSIZE / SAMPLESIZE, MATRIXSIZE / SAMPLESIZE);
    array<float, 2> averages(outputExtent, outputData.begin(), outputData.end());

    // Use tiles that are SAMPLESIZE x SAMPLESIZE.
    // Find the average of the values in each tile.
    // The only reference-type variable you can pass into the parallel_for_each call
    // is a concurrency::array.
    parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),
        [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)
    {
        // Copy the values of the tile into a tile-sized array.
        tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];
        tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];

        // Wait for the tile-sized array to load before you calculate the average.
        t_idx.barrier.wait();

        // If you remove the if statement, then the calculation executes for every
        // thread in the tile, and makes the same assignment to averages each time.
        if (t_idx.local[0] == 0 && t_idx.local[1] == 0) {
            for (int trow = 0; trow < SAMPLESIZE; trow++) {
                for (int tcol = 0; tcol < SAMPLESIZE; tcol++) {
                    averages(t_idx.tile[0],t_idx.tile[1]) += tileValues[trow][tcol];
                }
            }
            averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE * SAMPLESIZE);
        }
    });

    // Print out the results.
    // You cannot access the values in averages directly. You must copy them
    // back to a CPU variable.
    outputData = averages;
    for (int row = 0; row < outputSize; row++) {
        for (int col = 0; col < outputSize; col++) {
            std::cout << outputData[row*outputSize + col] << " ";
        }
        std::cout << "\n";
    }
    // Output for SAMPLESSIZE = 2 is:
    //  4.5  6.5  8.5 10.5
    // 20.5 22.5 24.5 26.5
    // 36.5 38.5 40.5 42.5
    // 52.5 54.5 56.5 58.5

    // Output for SAMPLESIZE = 4 is:
    // 13.5 17.5
    // 45.5 49.5
}

int main() {
    SamplingExample();
}
```

## <a name="race-conditions"></a>Condiciones de carrera

Puede ser tentador crear un `tile_static` variable denominada `total` y aumentar dicha variable para cada subproceso, similar al siguiente:

```cpp
// Do not do this.
tile_static float total;
total += matrix[t_idx];
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
```

El primer problema con este enfoque es que `tile_static` variables no pueden tener inicializadores. El segundo problema es que hay una condición de carrera en la asignación a `total`, porque todos los subprocesos del mosaico tienen acceso a la variable sin ningún orden determinado. Es posible programar un algoritmo para permitir sólo un subproceso tenga acceso a la total en cada barrera, tal como se muestra a continuación. Sin embargo, esta solución no es extensible.

```cpp
// Do not do this.
tile_static float total;
if (t_idx.local[0] == 0&& t_idx.local[1] == 0) {
    total = matrix[t_idx];
}
t_idx.barrier.wait();

if (t_idx.local[0] == 0&& t_idx.local[1] == 1) {
    total += matrix[t_idx];
}
t_idx.barrier.wait();

// etc.
```

## <a name="memory-fences"></a>Barreras de memoria

Hay dos tipos de accesos a memoria que deben estar sincronizadas: acceso a la memoria global y `tile_static` acceso a la memoria. Un `concurrency::array` objeto asigna solo memoria global. Un `concurrency::array_view` puede hacer referencia a la memoria global, `tile_static` memoria, o ambas, según cómo se construyó.  Hay dos tipos de memoria que deben sincronizarse:

- memoria global

- `tile_static`

Un *barrera de memoria* garantiza que están disponibles para otros subprocesos del mosaico de subprocesos tiene acceso a la memoria y que la memoria se ejecutan según el orden programado. Para asegurarse de esto, los compiladores y los procesadores no reordenan lecturas y escrituras a través de la barrera. En C++ AMP, se crea una barrera de memoria mediante una llamada a uno de estos métodos:

- [tile_barrier:: Wait (método)](reference/tile-barrier-class.md#wait): Crea una barrera alrededor tanto global y `tile_static` memoria.

- [Método tile_barrier::wait_with_all_memory_fence](reference/tile-barrier-class.md#wait_with_all_memory_fence): Crea una barrera alrededor tanto global y `tile_static` memoria.

- [Método tile_barrier::wait_with_global_memory_fence](reference/tile-barrier-class.md#wait_with_global_memory_fence): Crea una barrera alrededor únicamente la memoria global.

- [Método tile_barrier::wait_with_tile_static_memory_fence](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence): Crea una barrera alrededor únicamente `tile_static` memoria.

Una llamada a la barrera específica que necesite puede mejorar el rendimiento de la aplicación. El tipo de barrera influye en cómo el compilador y el hardware reordenan las instrucciones. Por ejemplo, si utiliza una barrera de memoria global, aplica accesos a memoria sólo globales y por lo tanto, el compilador y el hardware podrían cambiar el orden lee y escribe en `tile_static` variables en los dos lados de la barrera.

En el ejemplo siguiente, la barrera sincroniza las escrituras en `tileValues`, un `tile_static` variable. En este ejemplo, `tile_barrier::wait_with_tile_static_memory_fence` se llama en lugar de `tile_barrier::wait`.

```cpp
// Using a tile_static memory fence.
parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),
    [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)
{
    // Copy the values of the tile into a tile-sized array.
    tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];
    tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];

    // Wait for the tile-sized array to load before calculating the average.
    t_idx.barrier.wait_with_tile_static_memory_fence();

    // If you remove the if statement, then the calculation executes
    // for every thread in the tile, and makes the same assignment to
    // averages each time.
    if (t_idx.local[0] == 0&& t_idx.local[1] == 0) {
        for (int trow = 0; trow <SAMPLESIZE; trow++) {
            for (int tcol = 0; tcol <SAMPLESIZE; tcol++) {
                averages(t_idx.tile[0],t_idx.tile[1]) += tileValues[trow][tcol];
            }
        }
    averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
    }
});
```

## <a name="see-also"></a>Vea también

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[tile_static (Palabra clave)](../../cpp/tile-static-keyword.md)
