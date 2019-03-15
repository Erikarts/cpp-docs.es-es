---
title: Procedimiento Usar eventos de compilación en proyectos de MSBuild
ms.date: 11/04/2016
f1_keywords:
- msbuild.cpp.howto.usebuildevents
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
ms.openlocfilehash: 7678b975558b245fb730bff35fb156bf21d7f895
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814127"
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>Filtrar Usar eventos de compilación en proyectos de MSBuild

Un evento de compilación es un comando que MSBuild se realiza en una determinada fase del proceso de compilación. El *anterior a la compilación* evento se produce antes de que empiece la compilación; el *anterior a la vinculación* evento tiene lugar antes de iniciar el paso de vínculo; y la *posterior a la compilación* evento tiene lugar después de la compilación finaliza correctamente. Se produce un evento de compilación solo si se produce el paso de compilación asociada. Por ejemplo, el evento anterior a la vinculación no se produce si no se ejecuta el paso de vinculación.

Cada uno de los eventos de tres compilación se representa en un grupo de definiciones de elemento mediante un elemento command (`<Command>`) que se ejecuta y un elemento de mensaje (`<Message>`) que es que se muestran cuando **MSBuild** realiza el evento de compilación. Cada elemento es opcional y, si especifica varias veces el mismo elemento, la última aparición tiene prioridad.

Opcional *use compilación* elemento (`<`*eventos de compilación*`UseInBuild>`) se pueden especificar en un grupo de propiedades para indicar si se ejecuta el evento de compilación. El valor del contenido de un *use compilación* elemento sea **true** o **false**. De forma predeterminada, un evento de compilación se ejecuta a menos que el correspondiente *use compilación* elemento está establecido en `false`.

En la tabla siguiente se enumera cada elemento XML de eventos de compilación:

|Elemento XML|Descripción|
|-----------------|-----------------|
|`PreBuildEvent`|Este evento se ejecuta antes de que comience la compilación.|
|`PreLinkEvent`|Este evento se ejecuta antes de que comience el paso de vinculación.|
|`PostBuildEvent`|Este evento se ejecuta una vez finalizada la compilación.|

La siguiente tabla enumera cada *use compilación* elemento:

|Elemento XML|Descripción|
|-----------------|-----------------|
|`PreBuildEventUseInBuild`|Especifica si se debe ejecutar el *anterior a la compilación* eventos.|
|`PreLinkEventUseInBuild`|Especifica si se debe ejecutar el *anterior a la vinculación* eventos.|
|`PostBuildEventUseInBuild`|Especifica si se debe ejecutar el *posterior a la compilación* eventos.|

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se puede agregar dentro del elemento de proyecto del archivo myproject.vcxproj creado en [Tutorial: Usar MSBuild para crear un proyecto de Visual C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md). Un *anterior a la compilación* evento hace una copia de main.cpp; un *anterior a la vinculación* evento hace una copia de main.obj; y un *posterior a la compilación* evento hace una copia de myproject.exe. Si el proyecto se compiló con una configuración de lanzamiento, se ejecutan los eventos de compilación. Si el proyecto se compiló con una configuración de depuración, no se ejecutan los eventos de compilación.

```
<ItemDefinitionGroup>
  <PreBuildEvent>
    <Command>copy $(ProjectDir)main.cpp $(ProjectDir)copyOfMain.cpp</Command>
    <Message>Making a copy of main.cpp </Message>
  </PreBuildEvent>
  <PreLinkEvent>
<Command>copy $(ProjectDir)$(Configuration)\main.obj $(ProjectDir)$(Configuration)\copyOfMain.obj</Command>
    <Message>Making a copy of main.obj</Message>
  </PreLinkEvent>
  <PostBuildEvent>
<Command>copy $(ProjectDir)$(Configuration)\$(TargetFileName) $(ProjectDir)$(Configuration)\copyOfMyproject.exe</Command>
    <Message>Making a copy of myproject.exe</Message>
  </PostBuildEvent>
</ItemDefinitionGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
  <PreBuildEventUseInBuild>true</PreBuildEventUseInBuild>
  <PreLinkEventUseInBuild>true</PreLinkEventUseInBuild>
  <PostBuildEventUseInBuild>true</PostBuildEventUseInBuild>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
  <PreBuildEventUseInBuild>false</PreBuildEventUseInBuild>
  <PreLinkEventUseInBuild>false</PreLinkEventUseInBuild>
  <PostBuildEventUseInBuild>false</PostBuildEventUseInBuild>
</PropertyGroup>
```

## <a name="see-also"></a>Vea también

[MSBuild en la línea de comandos - C++](msbuild-visual-cpp.md)<br/>
[Tutorial: Uso de MSBuild para crear un proyecto de Visual C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)
