---
title: Instalación de la carga de trabajo de Linux para C++ en Visual Studio
description: En este artículo se describe cómo descargar, instalar y configurar la carga de trabajo de Linux para C++ en Visual Studio.
ms.date: 02/06/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: c01c8ddeeb8439a7610c0f6c7c11b608ab3675d8
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2019
ms.locfileid: "55763897"
---
# <a name="download-install-and-setup-the-linux-workload"></a>Descargar, instalar y configurar la carga de trabajo de Linux

Puede usar el IDE de Visual Studio en Windows para crear, editar y depurar proyectos de C++ que se ejecutan en un equipo físico Linux, una máquina virtual o el [subsistema Windows para Linux](/windows/wsl/about). Para cualquiera de estos escenarios, primero debe instalar la carga de trabajo de **Desarrollo de Linux con C++**.

## <a name="visual-studio-setup"></a>Instalación de Visual Studio

1. Escriba "Instalador de Visual Studio" en el cuadro de búsqueda de Windows: ![Cuadro de búsqueda de Windows](media/visual-studio-installer-search.png)
2. Busque el instalador en los resultados de la categoría **Aplicaciones** y haga doble clic en este. Cuando se abra el instalador, elija **Modificar** y después haga clic en la pestaña **Cargas de trabajo**. Desplácese hacia abajo hasta **Otros conjuntos de herramientas** y seleccione la carga de trabajo **Desarrollo de Linux con C++**.

   ![Carga de trabajo Visual C++ for Linux Development](media/linuxworkload.png)

1. Si utiliza CMake o tiene como destino plataformas incrustadas o IoT, vaya al panel **Detalles de la instalación** de la derecha, debajo de **Desarrollo de Linux con C++**, expanda **Componentes opcionales** y elija los componentes que necesita.

1. Haga clic en **Modificar** para continuar con la instalación.

## <a name="options-for-creating-a-linux-environment"></a>Opciones para crear un entorno Linux

Si no dispone de una máquina Linux, puede crear una máquina virtual Linux en Azure. Para obtener más información, vea [Inicio rápido: Creación de una máquina virtual Linux en Azure Portal](/azure/virtual-machines/linux/quick-create-portal).

Otra opción, en Windows 10, es activar el subsistema Windows para Linux. Para más información, vea la [guía de instalación de Windows 10](/windows/wsl/install-win10).

## <a name="linux-setup-ubuntu"></a>Instalación de Linux: Ubuntu

El equipo Linux de destino debe tener **openssh-server**, **g++**, **gdb** y **gdbserver** instalados y ssh daemon debe estar en ejecución. **ZIP** es necesario para realizar la sincronización automática de encabezados remotos con el equipo local para la compatibilidad con IntelliSense. Si estas aplicaciones aún no están instaladas, puede hacerlo como sigue:

1. En un símbolo del sistema del shell del equipo Linux, ejecute:

   `sudo apt-get install openssh-server g++ gdb gdbserver zip`

   Debido al comando sudo, es posible que se le pida la contraseña raíz.  Si es así, escríbala y continúe. Una vez que finalice, estarán instaladas las herramientas y los servicios requeridos.

1. Asegúrese de que el servicio ssh se esté ejecutando en el equipo Linux al ejecutar:

   `sudo service ssh start`

   Esto inicia el servicio y lo ejecuta en segundo plano, listo para aceptar conexiones.

## <a name="linux-setup-fedora"></a>Instalación de Linux: Fedora

La máquina de destino en la que se ejecuta Fedora usa el instalador de paquetes **dnf**. Para descargar **openssh-server**, **g++**, **gdb**, **gdbserver** y **zip** y reiniciar el demonio de ssh, siga estas instrucciones:

1. En un símbolo del sistema del shell del equipo Linux, ejecute:

   `sudo dnf install openssh-server gcc-g++ gdb gdb-gdbserver zip`

   Debido al comando sudo, es posible que se le pida la contraseña raíz.  Si es así, escríbala y continúe. Una vez que finalice, estarán instaladas las herramientas y los servicios requeridos.

1. Asegúrese de que el servicio ssh se esté ejecutando en el equipo Linux al ejecutar:

   `sudo systemctl start sshd`

   Esto inicia el servicio y lo ejecuta en segundo plano, listo para aceptar conexiones.

