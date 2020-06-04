---
title: Compatibilidad con MFC en proyectos ATL
ms.date: 11/04/2016
f1_keywords:
- vc.atl.addmfc
helpviewer_keywords:
- ATL projects, MFC support
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
ms.openlocfilehash: 0aece6805f1de987b0164f405e50b99fd706fef4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275430"
---
# <a name="mfc-support-in-atl-projects"></a>Compatibilidad con MFC en proyectos ATL

Si selecciona **compatibilidad con MFC** en el Asistente para proyectos ATL, el proyecto declara la aplicación como un objeto de aplicación MFC (clase). El proyecto se inicializa la biblioteca MFC y crea una instancia de una clase (clase *Nombre_proyecto*) que se deriva [CWinApp](../../mfc/reference/cwinapp-class.md).

Esta opción está disponible para proyectos DLL ATL sin atributos solo.

```
class CProjNameApp : public CWinApp
{
public:

// Overrides
    virtual BOOL InitInstance();
virtual int ExitInstance();
DECLARE_MESSAGE_MAP()
};

BEGIN_MESSAGE_MAP(CProjNameApp, CWinApp)
END_MESSAGE_MAP()

CProjNameApp theApp;

BOOL CProjNameApp::InitInstance()
{
    return CWinApp::InitInstance();

}

int CProjNameApp::ExitInstance()
{
    return CWinApp::ExitInstance();

}
```

Puede ver la clase de objeto de aplicación y su `InitInstance` y `ExitInstance` funciones en la vista de clases.

## <a name="see-also"></a>Vea también

[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)<br/>
[Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Configuraciones de proyecto ATL predeterminadas](../../atl/reference/default-atl-project-configurations.md)
