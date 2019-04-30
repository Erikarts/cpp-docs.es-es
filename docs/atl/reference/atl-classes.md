---
title: ATL clases y structs | Microsoft Docs
ms.date: 05/03/2018
helpviewer_keywords:
- classes [C++], ATL
- ATL, classes
ms.assetid: 7da42e2d-ac84-4506-92bd-502a86d68bdc
ms.openlocfilehash: 561d6cb41ca066f5a2435b4eb1e8710ccaa99ea1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62248945"
---
# <a name="atl-classes-and-structs"></a>Structs y clases ATL

Active Template Library (ATL) incluye las siguientes clases y structs. Para buscar una clase concreta por categoría, vea el [información general de clases ATL](../../atl/atl-class-overview.md).

|Clase o struct|Descripción|Archivo de encabezado|
|-----------|-----------------|-----------------|
|[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)|Contiene información utilizada para la representación a varios destinos, como una impresora, metarchivo o control ActiveX.|atlctl.h|
|[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)|Contiene los datos de la instancia de clase en código basado en ventanas en ATL.|atlbase.h|
|[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)|Usado por cualquier proyecto que usa ATL.|atlbase.h|
|[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)|Utilizado por el código relacionado con COM de ATL.| atlbase.h|
|[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)|Contiene información de tipo que se utiliza para describir un método o propiedad en una interfaz dispinterface.|atlcom.h|
|[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)|Contiene los datos utilizados por cada módulo ATL.|atlbase.h|
|[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|Utilizado por el código basado en ventanas en ATL.|atlbase.h|
|[CA2AEX](../../atl/reference/ca2aex-class.md)|Esta clase se utiliza por las macros de conversión de cadena CA2TEX y CT2AEX y la definición de tipo CA2A.|atlconv.h|
|[CA2CAEX](../../atl/reference/ca2caex-class.md)|Esta clase se usa macros de conversión de cadena CA2CTEX y CT2CAEX y la definición de tipo CA2CA.|atlconv.h|
|[CA2WEX](../../atl/reference/ca2wex-class.md)|Esta clase se utiliza por las macros de conversión de cadena CA2TEX, CA2CTEX, CT2WEX y CT2CWEX y la definición de tipo CA2W.|atlconv.h|
|[CAccessToken](../../atl/reference/caccesstoken-class.md)|Esta clase es un contenedor para un token de acceso.|atlsecurity.h|
|[CAcl](../../atl/reference/cacl-class.md)|Esta clase es un contenedor para una estructura ACL (lista de control de acceso).|atlsecurity.h|
|[CAdapt](../../atl/reference/cadapt-class.md)|Esta plantilla se utiliza para ajustar las clases que vuelven a definir el operador address-of para devolver algo distinto de la dirección del objeto.|atlcomcli.h|
|[CAtlArray](../../atl/reference/catlarray-class.md)|Esta clase implementa un objeto de matriz.|atlcoll.h|
|[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)|Esta clase implementa un servidor COM de subprocesamiento de modelo, agrupadas por subproceso.|atlbase.h|
|[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)|Esta clase proporciona métodos para implementar un servidor COM de subprocesamiento de modelo, agrupadas por subproceso.|atlbase.h|
|[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)|Esta clase se crean instancias en todos los proyectos ATL.|atlcore.h|
|[CAtlComModule](../../atl/reference/catlcommodule-class.md)|Esta clase implementa un módulo COM del servidor.|atlbase.h|
|[CAtlDebugInterfacesModule](../../atl/reference/catldebuginterfacesmodule-class.md)|Esta clase proporciona compatibilidad para interfaces de depuración.|atlbase.h|
|[CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)|Esta clase representa el módulo para un archivo DLL.|atlbase.h|
|[CAtlException](../../atl/reference/catlexception-class.md)|Esta clase define una excepción de ATL.|atlexcept.h|
|[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)|Esta clase representa el módulo de una aplicación.|atlbase.h|
|[CAtlFile](../../atl/reference/catlfile-class.md)|Esta clase proporciona un contenedor fino alrededor de la Windows API de administración de archivos.|atlfile.h|
|[CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)|Esta clase representa un archivo asignado a memoria, adición de un operador de conversión a los métodos de [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).|atlfile.h|
|[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)|Esta clase representa un archivo asignado a memoria.|atlfile.h|
|[CAtlList](../../atl/reference/catllist-class.md)|Esta clase proporciona métodos para crear y administrar un objeto de lista.|atlcoll.h|
|[CAtlMap](../../atl/reference/catlmap-class.md)|Esta clase proporciona métodos para crear y administrar un objeto de mapa.|atlcoll.h|
|[CAtlModule](../../atl/reference/catlmodule-class.md)|Esta clase proporciona métodos utilizados por varias clases de módulo ATL.|atlbase.h|
|[CAtlModuleT](../../atl/reference/catlmodulet-class.md)|Esta clase implementa un módulo de ATL.|atlbase.h|
|[CAtlPreviewCtrlImpl](../../atl/reference/catlpreviewctrlimpl-class.md)|Esta clase es una implementación de ATL de una ventana que se coloca en una ventana host proporcionada por el Shell de vista previa avanzada.|atlpreviewctrlimpl.h|
|[CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md)|Esta clase implementa un servicio.|atlbase.h|
|[CAtlTemporaryFile](../../atl/reference/catltemporaryfile-class.md)|Esta clase proporciona métodos para la creación y uso de un archivo temporal.|atlfile.h|
|[CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)|Esta clase proporciona un contenedor para las funciones de administrador de transacciones de Kernel (KTM).|atltransactionmanager.h|
|[CAtlWinModule](../../atl/reference/catlwinmodule-class.md)|Esta clase proporciona compatibilidad para los componentes de ventana ATL.|atlbase.h|
|[CAutoPtr](../../atl/reference/cautoptr-class.md)|Esta clase representa un objeto de puntero inteligente.|atlbase.h|
|[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)|Esta clase proporciona métodos útiles al construir una matriz de punteros inteligentes.|atlbase.h|
|[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)|Esta clase proporciona métodos, funciones estáticas y definiciones de tipos útiles al crear colecciones de punteros inteligentes.|atlcoll.h|
|[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)|Esta clase proporciona métodos útiles al construir una lista de punteros inteligentes.|atlcoll.h|
|[CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)|Esta clase representa un objeto de puntero inteligente con nuevo vector y elimina operadores.|atlbase.h|
|[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)|Esta clase proporciona métodos, funciones estáticas y definiciones de tipos útiles al crear colecciones con nuevo vector de punteros inteligentes y eliminar operadores.|atlcoll.h|
|[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)|Esta clase implementa un cuadro de diálogo (modal o no modal) que hospeda los controles ActiveX.|atlwin.h|
|[CAxWindow](../../atl/reference/caxwindow-class.md)|Esta clase proporciona métodos para manipular una ventana de hospedar un control ActiveX.|atlwin.h|
|[CAxWindow2T](../../atl/reference/caxwindow2t-class.md)|Esta clase proporciona métodos para manipular una ventana que hospeda un control ActiveX y también tiene compatibilidad para hospedar controles ActiveX con licencia.|atlwin.h|
|[CBindStatusCallback](../../atl/reference/cbindstatuscallback-class.md)|Esta clase implementa la interfaz `IBindStatusCallback` .|atlctl.h|
|[CComAggObject](../../atl/reference/ccomaggobject-class.md)|Esta clase implementa [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) para un objeto agregado.|atlcom.h|
|[CComAllocator](../../atl/reference/ccomallocator-class.md)|Esta clase proporciona métodos para administrar la memoria que usa COM rutinas de memoria.|atlbase.h|
|[CComApartment](../../atl/reference/ccomapartment-class.md)|Esta clase proporciona compatibilidad para administrar un apartamento de un módulo EXE agrupados por subproceso.|atlbase.h|
|[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)|Esta clase proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.|atlcore.h|
|[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)|A partir de ATL 7.0, `CComAutoThreadModule` está obsoleta: vea [ATL módulos](../../atl/atl-module-classes.md) para obtener más detalles.|atlbase.h|
|[CComBSTR](../../atl/reference/ccombstr-class.md)|Esta clase es un contenedor de cadenas BSTR.|atlbase.h|
|[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)|Esta clase implementa [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) para una interfaz desplazable.|atlcom.h|
|[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)|Esta clase implementa la [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) interfaz.|atlcom.h|
|[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)|Esta clase implementa la [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2) interfaz.|atlcom.h|
|[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)|Esta clase implementa la [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) interfaz y permite que los objetos que se creará en varios contenedores.|atlcom.h|
|[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)|Esta clase se deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y usa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un objeto único.|atlcom.h|
|[CComCoClass](../../atl/reference/ccomcoclass-class.md)|Esta clase proporciona métodos para crear instancias de una clase y obtener sus propiedades.|atlcom.h|
|[CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)|Esta clase proporciona los métodos necesarios para implementar un control compuesto.|atlctl.h|
|[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)|Esta clase implementa [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) mediante la delegación para el objeto propietario `IUnknown`.|atlcom.h|
|[CComControl](../../atl/reference/ccomcontrol-class.md)|Esta clase proporciona métodos para crear y administrar los controles ATL.|atlctl.h|
|[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)|Esta clase proporciona métodos para crear y administrar los controles ATL.|atlctl.h|
|[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)|Esta clase proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.|atlcore.h|
|[CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)|Esta clase proporciona métodos para bloquear y desbloquear un objeto de sección crítica.|atlbase.h|
|[CComCurrency](../../atl/reference/ccomcurrency-class.md)|Esta clase tiene métodos y operadores para crear y administrar un objeto CURRENCY.|atlcur.h|
|[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)|Esta clase almacena una matriz de `IUnknown` punteros.|atlcom.h|
|[CComEnum](../../atl/reference/ccomenum-class.md)|Esta clase define un objeto de enumerador COM basándose en una matriz.|atlcom.h|
|[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)|Esta clase proporciona la implementación de una interfaz de enumerador COM donde se almacenan los elementos que se va a enumerar en una matriz.|atlcom.h|
|[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)|Esta clase define un objeto de enumerador COM basándose en una colección de la biblioteca estándar de C++.|atlcom.h|
|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)|Esta clase proporciona los mismos métodos que [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) pero no proporciona una sección crítica.|atlcore.h|
|[CComGITPtr](../../atl/reference/ccomgitptr-class.md)|Esta clase proporciona métodos para trabajar con punteros de interfaz y la tabla de interfaz global (GIT).|atlbase.h|
|[CComHeap](../../atl/reference/ccomheap-class.md)|Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones de asignación de memoria COM.|ATLComMem.h|
|[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)|Una clase de puntero inteligente para administrar los punteros de montón.|atlbase.h|
|[CComModule](../../atl/reference/ccommodule-class.md)|A partir de ATL 7.0, `CComModule` está obsoleta: vea [ATL módulos](../../atl/atl-module-classes.md) para obtener más detalles.|atlbase.h|
|[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)|Esta clase proporciona métodos de subprocesos para aumentar y disminuir el valor de una variable.|atlbase.h|
|[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)|Esta clase proporciona métodos de subprocesos para aumentar y disminuir el valor de una variable, sin bloqueo de sección crítica o funcionalidad de desbloqueo.|atlbase.h|
|[CComObject](../../atl/reference/ccomobject-class.md)|Esta clase implementa `IUnknown` para un objeto no agregado.|atlcom.h|
|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)|Esta clase administra un recuento de referencias en el módulo que contiene su `Base` objeto.|atlcom.h|
|[CComObjectNoLock](../../atl/reference/ccomobjectnolock-class.md)|Esta clase implementa `IUnknown` para un objeto no agregado, pero no no incremento el módulo recuento de bloqueos en el constructor.|atlcom.h|
|[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)|Esta definición de tipo de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) se hace plantilla en el modelo del servidor de subprocesamiento predeterminado.|atlcom.h|
|[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)|Esta clase proporciona métodos para controlar la administración de recuento de referencia de objeto para objetos agregados y agregados.|atlcom.h|
|[CComObjectStack](../../atl/reference/ccomobjectstack-class.md)|Esta clase crea un objeto COM temporal y le proporciona una implementación básica de `IUnknown`.|atlcom.h|
|[CComPolyObject](../../atl/reference/ccompolyobject-class.md)|Esta clase implementa `IUnknown` para un objeto agregado o no agregado.|atlcom.h|
|[CComPtr](../../atl/reference/ccomptr-class.md)|Una clase de puntero inteligente para administrar los punteros de interfaz COM.|atlcomcli.h|
|[CComPtrBase](../../atl/reference/ccomptrbase-class.md)|Esta clase proporciona una base para las clases de puntero inteligente que usa las rutinas de memoria basado en COM.|atlcomcli.h|
|[CComQIPtr](../../atl/reference/ccomqiptr-class.md)|Una clase de puntero inteligente para administrar los punteros de interfaz COM.|atlcomcli.h|
|[CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)|Esta clase proporciona métodos, funciones estáticas y definiciones de tipos útiles al crear colecciones de punteros de interfaz COM.|atlcoll.h|
|[CComSafeArray](../../atl/reference/ccomsafearray-class.md)|Esta clase es un contenedor para el `SAFEARRAY Data Type` estructura.|atlsafe.h|
|[CComSafeArrayBound](../../atl/reference/ccomsafearraybound-class.md)|Esta clase es un contenedor para un `SAFEARRAYBOUND` estructura.|atlsafe.h|
|[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)|Esta clase administra la selección de subproceso para la clase [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).|atlbase.h|
|[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)|Esta clase proporciona métodos para aumentar y disminuir el valor de una variable.|atlbase.h|
|[CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)|Esta clase implementa una interfaz desplazable.|atlcom.h|
|[CComUnkArray](../../atl/reference/ccomunkarray-class.md)|Esta clase almacena `IUnknown` punteros y está diseñado para usarse como un parámetro a la [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) clase de plantilla.|atlcom.h|
|[CComVariant](../../atl/reference/ccomvariant-class.md)|Esta clase encapsula el tipo de variante, que proporciona a un miembro que indica el tipo de datos almacenados.|atlcomcli.h|
|[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)|Esta clase implementa una ventana dentro de otro objeto.|atlwin.h|
|[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)|Esta clase proporciona métodos para administrar la memoria utilizando las rutinas de memoria de CRT.|atlcore.h|
|[CCRTHeap](../../atl/reference/ccrtheap-class.md)|Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones del montón de CRT.|atlmem.h|
|[CDacl](../../atl/reference/cdacl-class.md)|Esta clase es un contenedor para una estructura DACL (lista de control de acceso discrecional).|atlsecurity.h|
|[CDebugReportHook (clase)](../../atl/reference/cdebugreporthook-class.md)|Utilice esta clase para enviar informes de depuración a una canalización con nombre.|atlutil.h|
|[CDefaultCharTraits](../../atl/reference/cdefaultchartraits-class.md)|Esta clase proporciona dos funciones estáticas para la conversión de caracteres entre mayúsculas y minúsculas.|atlcoll.h|
|[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)|Esta clase proporciona funciones de comparación de elemento de predeterminado.|atlcoll.h|
|[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)|Esta clase proporciona funciones y métodos predeterminados para una clase de colección.|atlcoll.h|
|[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)|Esta clase proporciona una función estática para calcular los valores hash.|atlcoll.h|
|[CDialogImpl](../../atl/reference/cdialogimpl-class.md)|Esta clase proporciona métodos para crear un cuadro de diálogo modal o no modal.|atlwin.h|
|[CDynamicChain](../../atl/reference/cdynamicchain-class.md)|Esta clase proporciona métodos que admiten el encadenamiento dinámico de mapas de mensajes.|atlwin.h|
|[CElementTraits](../../atl/reference/celementtraits-class.md)|Esta clase se utiliza por las clases de colección para proporcionar funciones y métodos para mover, copiar, comparaciones y operaciones hash.|atlcoll.h|
|[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)|Esta clase proporciona copia de forma predeterminada y move los métodos para una clase de colección.|atlcoll.h|
|[CFirePropNotifyEvent](../../atl/reference/cfirepropnotifyevent-class.md)|Esta clase proporciona métodos para notificar el receptor del contenedor con respecto a los cambios de propiedad de control.|atlctl.h|
|[CGlobalHeap](../../atl/reference/cglobalheap-class.md)|Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones del montón global de Win32.|atlmem.h|
|[CHandle](../../atl/reference/chandle-class.md)|Esta clase proporciona métodos para crear y usar un identificador de objeto.|atlbase.h|
|[CHeapPtr](../../atl/reference/cheapptr-class.md)|Una clase de puntero inteligente para administrar los punteros de montón.|atlcore.h|
|[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)|Esta clase constituye la base de varias clases de puntero inteligente de montón.|atlcore.h|
|[CHeapPtrElementTraits (clase)](../../atl/reference/cheapptrelementtraits-class.md)|Esta clase proporciona métodos, funciones estáticas y definiciones de tipos útiles al crear colecciones de punteros del montón.|atlcoll.h|
|[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)|Esta clase proporciona métodos útiles al construir una lista de punteros del montón.|atlcoll.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|proporciona compatibilidad con mapas de bits mejorada, incluida la capacidad para cargar y guardar imágenes en los formatos GIF, JPEG, BMP y gráficos de red portátiles (PNG).|atlimage.h|
|[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)|Esta clase proporciona métodos útiles al construir una matriz de punteros de interfaz COM.|atlcoll.h|
|[CInterfaceList](../../atl/reference/cinterfacelist-class.md)|Esta clase proporciona métodos útiles al construir una lista de punteros de interfaz COM.|atlcoll.h|
|[CLocalHeap](../../atl/reference/clocalheap-class.md)|Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones del montón local de Win32.|atlmem.h|
|[CMessageMap](../../atl/reference/cmessagemap-class.md)|Esta clase permite que los mapas de mensajes de un objeto para tener acceso a otro objeto.|atlwin.h|
|[CNonStatelessWorker (clase)](../../atl/reference/cnonstatelessworker-class.md)|Recibe solicitudes de un grupo de subprocesos y los pasa a un objeto de trabajo que se crea y destruye en cada solicitud.|atlutil.h|
|[CNoWorkerThread (clase)](../../atl/reference/cnoworkerthread-class.md)|Utilice esta clase como argumento para el `MonitorClass` las clases de caché de parámetro de plantilla si desea deshabilitar el mantenimiento de la caché dinámica.|atlutil.h|
|[CPathT (clase)](../../atl/reference/cpatht-class.md)|Esta clase representa una ruta de acceso.|atlpath.h|
|[CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)|Esta clase proporciona métodos de forma predeterminada y las funciones de una clase de colección formado por tipos de datos primitivos.|atlcoll.h|
|[CPrivateObjectSecurityDesc](../../atl/reference/cprivateobjectsecuritydesc-class.md)|Esta clase representa un objeto de descriptor de seguridad de objeto privado.|atlsecurity.h|
|[CRBMap](../../atl/reference/crbmap-class.md)|Esta clase representa una estructura de asignación, mediante un árbol binario rojo-negro.|atlcoll.h|
|[CRBMultiMap](../../atl/reference/crbmultimap-class.md)|Esta clase representa una estructura de asignación que permite que cada clave que se va a asociar a más de un valor, utilizando un árbol binario rojo-negro.|atlcoll.h|
|[CRBTree](../../atl/reference/crbtree-class.md)|Esta clase proporciona métodos para la creación y uso de un árbol rojo-negro.|atlcoll.h|
|[CRegKey](../../atl/reference/cregkey-class.md)|Esta clase proporciona métodos para manipular las entradas del registro del sistema.|atlbase.h|
|[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)|Esta clase proporciona la función de creación de un subproceso de CRT. Utilice esta clase si el subproceso va a usar las funciones de CRT.|atlbase.h|
|[CSacl](../../atl/reference/csacl-class.md)|Esta clase es un contenedor para una estructura SACL (lista de control de acceso del sistema).|atlsecurity.h|
|[CSecurityAttributes](../../atl/reference/csecurityattributes-class.md)|Esta clase es un contenedor fino para la `SECURITY_ATTRIBUTES` estructura.|atlsecurity.h|
|[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)|Esta clase es un contenedor para el `SECURITY_DESCRIPTOR` estructura.|atlsecurity.h|
|[CSid](../../atl/reference/csid-class.md)|Esta clase es un contenedor para un `SID` estructura (identificador de seguridad).|atlsecurity.h|
|[CSimpleArray](../../atl/reference/csimplearray-class.md)|Esta clase proporciona métodos para administrar una matriz simple.|atlsimpcoll.h|
|[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)|Esta clase es una aplicación auxiliar para el [CSimpleArray](../../atl/reference/csimplearray-class.md) clase.|atlsimpcoll.h|
|[CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)|Esta clase es una aplicación auxiliar para el [CSimpleArray](../../atl/reference/csimplearray-class.md) clase.|atlsimpcoll.h|
|[CSimpleDialog](../../atl/reference/csimpledialog-class.md)|Esta clase implementa un cuadro de diálogo modal básica.|atlwin.h|
|[CSimpleMap](../../atl/reference/csimplemap-class.md)|Esta clase proporciona compatibilidad para una matriz de asignación simple.|atlsimpcoll.h|
|[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)|Esta clase es una aplicación auxiliar para el [CSimpleMap](../../atl/reference/csimplemap-class.md) clase.|atlsimpcoll.h|
|[CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)|Esta clase es una aplicación auxiliar para el [CSimpleMap](../../atl/reference/csimplemap-class.md) clase.|atlsimpcoll.h|
|[CSnapInItemImpl](../../atl/reference/csnapinitemimpl-class.md)|Esta clase proporciona métodos para implementar un objeto de nodo del complemento.|atlsnap.h|
|[CSnapInPropertyPageImpl](../../atl/reference/csnapinpropertypageimpl-class.md)|Esta clase proporciona métodos para implementar un objeto de la página de propiedades del complemento.|atlsnap.h|
|[CStockPropImpl](../../atl/reference/cstockpropimpl-class.md)|Esta clase proporciona métodos para la compatibilidad con los valores de propiedad estándar.|atlctl.h|
|[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)|Esta clase proporciona funciones estáticas usadas por las clases de colección para almacenar `CString` objetos.|cstringt.h|
|[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)|Esta clase proporciona funciones estáticas relacionados con las cadenas almacenadas en objetos de clase de colección. Es similar a [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), pero realiza comparaciones entre mayúsculas y minúsculas.|atlcoll.h|
|[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)|Esta clase proporciona funciones estáticas relacionados con las cadenas almacenadas en objetos de clase de colección. Los objetos de cadena se tratan como referencias.|atlcoll.h|
|[CThreadPool (clase)](../../atl/reference/cthreadpool-class.md)|Esta clase proporciona un grupo de subprocesos de trabajo que procesan una cola de elementos de trabajo.|atlutil.h|
|[CTokenGroups](../../atl/reference/ctokengroups-class.md)|Esta clase es un contenedor para el `TOKEN_GROUPS` estructura.|atlsecurity.h|
|[CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md)|Esta clase es un contenedor para el `TOKEN_PRIVILEGES` estructura.|atlsecurity.h|
|[CUrl (clase)](../../atl/reference/curl-class.md)|Esta clase representa una dirección URL. Permite manipular cada elemento de la dirección URL independientemente de los demás si una dirección URL existente de análisis de cadena o creación de una cadena desde el principio.|atlutil.h|
|[CW2AEX](../../atl/reference/cw2aex-class.md)|Esta clase se utiliza por las macros de conversión de cadena CT2AEX, CW2TEX, CW2CTEX y CT2CAEX y la definición de tipo CW2A.|atlconv.h|
|[CW2CWEX](../../atl/reference/cw2cwex-class.md)|Esta clase se utiliza por las macros de conversión de cadena CW2CTEX y CT2CWEX y la definición de tipo CW2CW.|atlconv.h|
|[CW2WEX](../../atl/reference/cw2wex-class.md)|Esta clase se utiliza por las macros de conversión de cadena CW2TEX y CT2WEX y la definición de tipo CW2W.|atlconv.h|
|[CWin32Heap](../../atl/reference/cwin32heap-class.md)|Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones de asignación del montón de Win32.|atlmem.h|
|[CWindow](../../atl/reference/cwindow-class.md)|Esta clase proporciona métodos para manipular una ventana.|atlwin.h|
|[CWindowImpl](../../atl/reference/cwindowimpl-class.md)|Esta clase proporciona métodos para crear o subclases de una ventana.|atlwin.h|
|[CWinTraits](../../atl/reference/cwintraits-class.md)|Esta clase proporciona un método de normalización de los estilos usados al crear un objeto de ventana.|atlwin.h|
|[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)|Esta clase proporciona un método de normalización de los estilos usados al crear un objeto de ventana.|atlwin.h|
|[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)|Esta clase proporciona métodos para registrar información de una clase de ventana.|atlwin.h|
|[CWorkerThread (clase)](../../atl/reference/cworkerthread-class.md)|Esta clase crea un subproceso de trabajo o usa uno existente, espera en uno o varios identificadores de objeto de kernel y ejecuta una función de cliente especificada cuando se señala a uno de los controladores.|atlutil.h|
|[IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)|Esta clase representa una interfaz para un `CreateInstance` método.|atlbase.h|
|[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)|Esta clase representa la interfaz a un administrador de memoria.|atlmem.h|
|[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)|Esta interfaz proporciona métodos para especificar las características del control hospedado o contenedor.|atlbase.h, ATLIFace.h|
|[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)|Esta interfaz implementa las propiedades de ambiente complementarias para un control hospedado.|atlbase.h, ATLIFace.h|
|[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)|Esta interfaz proporciona métodos para manipular un control y su objeto de host.|atlbase.h, ATLIFace.h|
|[IAxWinHostWindowLic](../../atl/reference/iaxwinhostwindowlic-interface.md)|Esta interfaz proporciona métodos para manipular un control con licencia y su objeto de host.|atlbase.h, ATLIFace.h|
|[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)|Esta clase proporciona métodos utilizados por una clase de colección.|atlcom.h|
|[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)|Esta clase implementa un contenedor de punto de conexión para administrar una colección de [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) objetos.|atlcom.h|
|[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)|Esta clase implementa un punto de conexión.|atlcom.h|
|[IDataObjectImpl](../../atl/reference/idataobjectimpl-class.md)|Esta clase proporciona métodos para admitir la transferencia de datos uniforme y administración de conexiones.|atlctl.h|
|[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)|Esta clase proporciona una implementación predeterminada para el `IDispatch` parte de una interfaz dual.|atlcom.h|
|[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)|Esta clase proporciona las implementaciones de la `IDispatch` métodos.|atlcom.h|
|[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)|Esta clase proporciona las implementaciones de la `IDispatch` métodos sin obtener información de tipo de una biblioteca de tipos.|atlcom.h|
|[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)|Interfaz para el análisis de HTML de Microsoft y el motor de representación.|atlbase.h, ATLIFace.h|
|[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)|Esta clase define una interfaz de enumerador basándose en una colección de la biblioteca estándar de C++.|atlcom.h|
|[IObjectSafetyImpl](../../atl/reference/iobjectsafetyimpl-class.md)|Esta clase proporciona una implementación predeterminada de la `IObjectSafety` interfaz para permitir que un cliente recuperar y establecer niveles de seguridad de un objeto.|atlctl.h|
|[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)|Esta clase proporciona métodos que permiten a un objeto para comunicarse con su sitio.|atlcom.h|
|[IOleControlImpl](../../atl/reference/iolecontrolimpl-class.md)|Esta clase proporciona una implementación predeterminada de la `IOleControl` interfaz e implementa `IUnknown`.|atlctl.h|
|[IOleInPlaceActiveObjectImpl](../../atl/reference/ioleinplaceactiveobjectimpl-class.md)|Esta clase proporciona métodos para ayudar a la comunicación entre un control in situ y su contenedor.|atlctl.h|
|[IOleInPlaceObjectWindowlessImpl](../../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)|Esta clase implementa `IUnknown` y proporciona métodos que permiten un control sin ventanas para recibir los mensajes de ventana y participar en operaciones de arrastrar y colocar.|atlctl.h|
|[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)|Esta clase implementa `IUnknown` y es la interfaz principal a través del cual se comunica un contenedor con un control.|atlctl.h|
|[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)|Esta clase implementa `IUnknown` y permite que un cliente tener acceso a la información de las páginas de propiedades de un objeto.|atlctl.h|
|[IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)|Esta clase implementa `IUnknown` y permite que un objeto guardar sus propiedades en una bolsa de propiedades proporcionados por el cliente.|atlcom.h|
|[IPersistStorageImpl](../../atl/reference/ipersiststorageimpl-class.md)|Esta clase implementa la [IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage) interfaz.|atlcom.h|
|[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)|Esta clase implementa `IUnknown` y proporciona una implementación predeterminada de la [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interfaz.|atlcom.h|
|[IPointerInactiveImpl](../../atl/reference/ipointerinactiveimpl-class.md)|Esta clase implementa `IUnknown` y [IPointerInactive](/windows/desktop/api/ocidl/nn-ocidl-ipointerinactive) métodos de interfaz.|atlctl.h|
|[IPropertyNotifySinkCP](../../atl/reference/ipropertynotifysinkcp-class.md)|Esta clase expone la [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) interfaz como una interfaz de salida en un objeto conectable.|atlctl.h|
|[IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)|Esta clase implementa `IUnknown` y hereda la implementación predeterminada de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).|atlctl.h|
|[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)|Esta clase implementa `IUnknown` y proporciona una implementación predeterminada de la [IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage) interfaz.|atlctl.h|
|[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md)|Esta clase proporciona una implementación predeterminada de la [IProvideClassInfo](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo) y [IProvideClassInfo2](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo2) métodos.|atlcom.h|
|[IQuickActivateImpl](../../atl/reference/iquickactivateimpl-class.md)|Esta clase combina la inicialización del control de contenedores en una sola llamada.|atlctl.h|
|[IRunnableObjectImpl](../../atl/reference/irunnableobjectimpl-class.md)|Esta clase implementa `IUnknown` y proporciona una implementación predeterminada de la [IRunnableObject](/windows/desktop/api/objidl/nn-objidl-irunnableobject) interfaz.|atlctl.h|
|[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)|Esta clase proporciona una implementación predeterminada de la `IServiceProvider` interfaz.|atlcom.h|
|[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)|Esta clase implementa `IUnknown` y proporciona una implementación predeterminada de la [ISpecifyPropertyPages](/windows/desktop/api/ocidl/nn-ocidl-ispecifypropertypages) interfaz.|atlcom.h|
|[ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md)|Esta clase proporciona una implementación predeterminada de la `ISupportErrorInfo Interface` interfaz y se puede usar cuando solo una sola interfaz genera errores en un objeto.|atlcom.h|
|[IThreadPoolConfig (interfaz)](../../atl/reference/ithreadpoolconfig-interface.md)|Esta interfaz proporciona métodos para configurar un grupo de subprocesos.|atlutil.h|
|[IViewObjectExImpl](../../atl/reference/iviewobjecteximpl-class.md)|Esta clase implementa `IUnknown` y proporciona implementaciones predeterminadas de la [IViewObject](/windows/desktop/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/desktop/api/oleidl/nn-oleidl-iviewobject2), y [IViewObjectEx](/windows/desktop/api/ocidl/nn-ocidl-iviewobjectex) interfaces.|atlctl.h|
|[IWorkerThreadClient (interfaz)](../../atl/reference/iworkerthreadclient-interface.md)|`IWorkerThreadClient` es la interfaz implementada por los clientes de la [CWorkerThread](../../atl/reference/cworkerthread-class.md) clase.|atlutil.h|
|[_U_MENUorID](../../atl/reference/u-menuorid-class.md)|Esta clase proporciona contenedores para `CreateWindow` y `CreateWindowEx`.|atlwin.h|
|[_U_RECT](../../atl/reference/u-rect-class.md)|Esta clase de adaptador de argumento permite `RECT` punteros o referencias a pasarse a una función que se implementa en términos de punteros.|atlwin.h|
|[_U_STRINGorID](../../atl/reference/u-stringorid-class.md)|Esta clase de adaptador de argumento permite que los nombres de recursos (LPCTSTRs) o identificadores de recursos (unidades) que se pasará a una función sin necesidad de convertir el identificador en una cadena mediante la macro MAKEINTRESOURCE al llamador.|atlwin.h|
|[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)|Esta clase proporciona la función de creación de un subproceso de Windows. Utilice esta clase si el subproceso no va a usar las funciones de CRT.|atlbase.h|

## <a name="see-also"></a>Vea también

[Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md)<br/>
[Funciones](../../atl/reference/atl-functions.md)<br/>
[Variables globales](../../atl/reference/atl-global-variables.md)<br/>
[Typedefs](../../atl/reference/atl-typedefs.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
