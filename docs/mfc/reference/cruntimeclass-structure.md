---
title: CRuntimeClass (estructura)
ms.date: 11/04/2016
f1_keywords:
- CRuntimeClass
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
ms.openlocfilehash: 92979a10c18d9759e0ecc9f0785e56a97c0f0642
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372054"
---
# <a name="cruntimeclass-structure"></a>CRuntimeClass (estructura)

Cada clase derivada de `CObject` está asociado con un `CRuntimeClass` estructura que puede usar para obtener información acerca de su clase base o de un objeto en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```
struct CRuntimeClass
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CRuntimeClass::CreateObject](#createobject)|Crea un objeto durante el tiempo de ejecución.|
|[CRuntimeClass::FromName](#fromname)|Crea un objeto durante el tiempo de ejecución mediante el nombre de clase conocidas.|
|[CRuntimeClass::IsDerivedFrom](#isderivedfrom)|Determina si la clase se deriva de la clase especificada.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CRuntimeClass::m_lpszClassName](#m_lpszclassname)|Nombre de la clase.|
|[CRuntimeClass::m_nObjectSize](#m_nobjectsize)|Tamaño del objeto en bytes.|
|[CRuntimeClass::m_pBaseClass](#m_pbaseclass)|Un puntero a la `CRuntimeClass` estructura de la clase base.|
|[CRuntimeClass::m_pfnCreateObject](#m_pfncreateobject)|Un puntero a la función que crea el objeto de forma dinámica.|
|[CRuntimeClass::m_pfnGetBaseClass](#m_pfngetbaseclass)|Devuelve el `CRuntimeClass` estructurar (solo disponible cuando dinámicamente vinculado).|
|[CRuntimeClass::m_wSchema](#m_wschema)|El número de esquema de la clase.|

## <a name="remarks"></a>Comentarios

`CRuntimeClass` es una estructura y, por tanto, no tiene una clase base.

La capacidad para determinar la clase de un objeto en tiempo de ejecución es útil cuando se necesita la comprobación de argumentos de función de tipo adicional, o cuando se debe escribir código especial basado en la clase de un objeto. Información de clases en tiempo de ejecución no se admite directamente en el lenguaje C++.

`CRuntimeClass` Proporciona información sobre el objeto relacionado de C++, por ejemplo, un puntero a la `CRuntimeClass` de la clase base y el nombre de clase ASCII de la clase relacionada. Esta estructura también implementa varias funciones que pueden usarse para crear dinámicamente objetos, que especifica el tipo de objeto mediante un nombre conocido, y determinar si la clase relacionada se deriva de una clase específica.

Para obtener más información sobre el uso de `CRuntimeClass`, consulte el artículo [acceso a información de clase de tiempo de ejecución](../../mfc/accessing-run-time-class-information.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CRuntimeClass`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="createobject"></a>  CRuntimeClass::CreateObject

Llame a esta función para crear dinámicamente la clase especificada durante el tiempo de ejecución.

```
CObject* CreateObject();

static CObject* PASCAL CreateObject(LPCSTR lpszClassName);

static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parámetros

*lpszClassName*<br/>
El nombre conocido de la clase que se va a crear.

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto recién creado, o NULL si el nombre de clase no se encuentra o no hay memoria suficiente para crear el objeto.

### <a name="remarks"></a>Comentarios

Las clases derivadas de `CObject` puede admitir la creación dinámica, que es la capacidad para crear un objeto de una clase especificada en tiempo de ejecución. Documento, vista y las clases de marco, por ejemplo, deben admitir la creación dinámica. Para obtener más información sobre la creación dinámica y la `CreateObject` miembro, vea [CObject (clase)](../../mfc/using-cobject.md) y [CObject (clase): Especificar los niveles de funcionalidad](../../mfc/specifying-levels-of-functionality.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsDerivedFrom](#isderivedfrom).

##  <a name="fromname"></a>  CRuntimeClass::FromName

Llame a esta función para recuperar el `CRuntimeClass` estructura asociada con el nombre conocido.

```
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);

static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parámetros

*lpszClassName*<br/>
El nombre conocido de una clase derivada de `CObject`.

### <a name="return-value"></a>Valor devuelto

Un puntero a un `CRuntimeClass` objeto se corresponde con el nombre que se pasa *lpszClassName*. La función devuelve NULL si se encontró ningún nombre de clase correspondiente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]

##  <a name="isderivedfrom"></a>  CRuntimeClass::IsDerivedFrom

Llame a esta función para determinar si la clase que realiza la llamada se deriva de la clase especificada en el *pBaseClass* parámetro.

```
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;
```

### <a name="parameters"></a>Parámetros

*pBaseClass*<br/>
El nombre conocido de una clase derivada de `CObject`.

### <a name="return-value"></a>Valor devuelto

TRUE si la llamada a la clase `IsDerivedFrom` se deriva de la base de clase cuya `CRuntimeClass` estructura está especificado como un parámetro; de lo contrario, FALSE.

### <a name="remarks"></a>Comentarios

La relación viene determinada por el "recorrido" de la clase del miembro de la cadena de las clases derivadas hasta la parte superior. Esta función solo devuelve FALSE si se encuentra ninguna coincidencia para la clase base.

> [!NOTE]
>  Para usar el `CRuntimeClass` estructura, debe incluir la macro IMPLEMENT_DYNAMIC, IMPLEMENT_DYNCREATE o IMPLEMENT_SERIAL en la implementación de la clase para el que desea recuperar información sobre los objetos de tiempo de ejecución.

Para obtener más información sobre el uso de `CRuntimeClass`, consulte el artículo [CObject (clase): Acceso a la información de clase en tiempo de ejecución](../../mfc/accessing-run-time-class-information.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]

##  <a name="m_lpszclassname"></a>  CRuntimeClass::m_lpszClassName

Una cadena terminada en null que contiene el nombre de clase de ASCII.

### <a name="remarks"></a>Comentarios

Este nombre se puede usar para crear una instancia de la clase utilizando el `FromName` función miembro.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsDerivedFrom](#isderivedfrom).

##  <a name="m_nobjectsize"></a>  CRuntimeClass::m_nObjectSize

El tamaño del objeto, en bytes.

### <a name="remarks"></a>Comentarios

Si el objeto tiene los miembros de datos que señalan a la memoria asignada, no se incluye el tamaño de la memoria.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsDerivedFrom](#isderivedfrom).

##  <a name="m_pbaseclass"></a>  CRuntimeClass::m_pBaseClass

Si la aplicación se vincula estáticamente a MFC, este miembro de datos contiene un puntero a la `CRuntimeClass` estructura de la clase base.

### <a name="remarks"></a>Comentarios

Si la aplicación se vincula dinámicamente a la biblioteca MFC, vea [m_pfnGetBaseClass](#m_pfngetbaseclass).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsDerivedFrom](#isderivedfrom).

##  <a name="m_pfncreateobject"></a>  CRuntimeClass::m_pfnCreateObject

Un puntero a función al constructor predeterminado que crea un objeto de la clase.

### <a name="remarks"></a>Comentarios

This (puntero) solo es válida si la clase admite la creación dinámica; en caso contrario, la función devuelve NULL.

##  <a name="m_pfngetbaseclass"></a>  CRuntimeClass::m_pfnGetBaseClass

Si la aplicación utiliza la biblioteca MFC como un archivo DLL compartido, este miembro de datos apunta a una función que devuelve el `CRuntimeClass` estructura de la clase base.

### <a name="remarks"></a>Comentarios

Si la aplicación se vincula estáticamente a la biblioteca MFC, vea [m_pBaseClass](#m_pbaseclass).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsDerivedFrom](#isderivedfrom).

##  <a name="m_wschema"></a>  CRuntimeClass::m_wSchema

El número de esquema (-1 para las clases de objetos no serializables).

### <a name="remarks"></a>Comentarios

Para obtener más información sobre los números de esquema, vea el [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [IsDerivedFrom](#isderivedfrom).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CObject::GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)<br/>
[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)<br/>
[RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)<br/>
[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)<br/>
[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)<br/>
[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)
