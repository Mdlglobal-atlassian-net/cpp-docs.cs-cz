---
title: Ccommodule – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComModule
- ATLBASE/ATL::CComModule
- ATLBASE/ATL::CComModule::GetClassObject
- ATLBASE/ATL::CComModule::GetModuleInstance
- ATLBASE/ATL::CComModule::GetResourceInstance
- ATLBASE/ATL::CComModule::GetTypeLibInstance
- ATLBASE/ATL::CComModule::Init
- ATLBASE/ATL::CComModule::RegisterClassHelper
- ATLBASE/ATL::CComModule::RegisterClassObjects
- ATLBASE/ATL::CComModule::RegisterServer
- ATLBASE/ATL::CComModule::RegisterTypeLib
- ATLBASE/ATL::CComModule::RevokeClassObjects
- ATLBASE/ATL::CComModule::Term
- ATLBASE/ATL::CComModule::UnregisterClassHelper
- ATLBASE/ATL::CComModule::UnregisterServer
- ATLBASE/ATL::CComModule::UpdateRegistryClass
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CComModule::m_csObjMap
- ATLBASE/ATL::CComModule::m_csTypeInfoHolder
- ATLBASE/ATL::CComModule::m_csWindowCreate
- ATLBASE/ATL::CComModule::m_hInst
- ATLBASE/ATL::CComModule::m_hInstResource
- ATLBASE/ATL::CComModule::m_hInstTypeLib
- ATLBASE/ATL::CComModule::m_pObjMap
dev_langs:
- C++
helpviewer_keywords:
- CComModule class
- DLL modules [C++], ATL
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e1ee6ee76840774fd750df95f73c105c059cae59
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196518"
---
# <a name="ccommodule-class"></a>Ccommodule – třída
Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComModule : public _ATL_MODULE
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComModule::GetClassObject](#getclassobject)|Vytvoří objekt zadaným identifikátorem CLSID. Pro knihovny DLL pouze.|  
|[CComModule::GetModuleInstance](#getmoduleinstance)|Vrátí `m_hInst`.|  
|[CComModule::GetResourceInstance](#getresourceinstance)|Vrátí `m_hInstResource`.|  
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|Vrátí `m_hInstTypeLib`.|  
|[V: CComModule::Init](#init)|Inicializuje datové členy.|  
|[CComModule::RegisterClassHelper](#registerclasshelper)|Zadá objektu standardní třídu registraci v registru systému.|  
|[CComModule::RegisterClassObjects](#registerclassobjects)|Zaregistruje objekt třídy. Pro pouze exe.|  
|[CComModule::RegisterServer](#registerserver)|Aktualizuje systémového registru pro jednotlivé objekty v mapě objektů.|  
|[CComModule::RegisterTypeLib](#registertypelib)|Zaregistruje knihovnu typů.|  
|[CComModule::RevokeClassObjects](#revokeclassobjects)|Odebere objekt třídy. Pro pouze exe.|  
|[Ccommodule::TERM.](#term)|Verze datové členy.|  
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|Odebere registraci standardní třídu objektu ze systémového registru.|  
|[CComModule::UnregisterServer](#unregisterserver)|Zruší registraci jednotlivých objektů v mapě objektů.|  
|[CComModule::UpdateRegistryClass](#updateregistryclass)|Zaregistruje nebo zruší registraci registrace standardní třídy objektu.|  
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Spustí skript, které jsou obsaženy v určený prostředek k registraci nebo zrušení registrace objektu.|  
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Staticky odkazuje na komponentu ATL registru. Spustí skript, které jsou obsaženy v určený prostředek k registraci nebo zrušení registrace objektu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComModule::m_csObjMap](#m_csobjmap)|Zajišťuje synchronizované přístup k informacím o objektu map.|  
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|Zajišťuje synchronizované přístup na informace knihovny typů.|  
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|Zajišťuje synchronizované přístup k informacím o třídě okna a statická data použít při vytváření okna.|  
|[CComModule::m_hInst](#m_hinst)|Obsahuje popisovač instance modulu.|  
|[CComModule::m_hInstResource](#m_hinstresource)|Ve výchozím nastavení obsahuje popisovač instance modulu.|  
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|Ve výchozím nastavení obsahuje popisovač instance modulu.|  
|[CComModule::m_pObjMap](#m_pobjmap)|Odkazuje na objekt map udržuje instancí modulu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato třída je zastaralá a Průvodce generování kódu ATL nyní používá [catlautothreadmodule –](../../atl/reference/catlautothreadmodule-class.md) a [catlmodule –](../../atl/reference/catlmodule-class.md) odvozené třídy. Zobrazit [ATL – třídy modulů](../../atl/atl-module-classes.md) Další informace. Informace, které následuje je pro použití s aplikacemi, vytvoří se staršími verzemi sady ATL. `CComModule` je stále součástí knihovny ATL pro zpětnou funkci.  
  
 `CComModule` implementuje server modulu COM, umožňuje klientům přístup k součástem modulu. `CComModule` podporuje knihovny DLL (v procesu) a moduly EXE (místní).  
  
 A `CComModule` instance používá mapování objektu udržovat sadu definic objektů třídy. Toto mapování objektu je implementovaný jako pole `_ATL_OBJMAP_ENTRY` struktury a obsahuje informace pro:  
  
-   Zadávání a odebírání popisy objektů v systémovém registru.  
  
-   Vytvoření instance objektů prostřednictvím objekt pro vytváření tříd.  
  
-   V komponentě navázání komunikace mezi klientem a kořenový objekt.  
  
-   Provádí správu životnosti objektů tříd.  
  
 Když spustíte AppWizard knihovny ATL modelu COM, průvodce automaticky generuje `_Module`, globální instanci `CComModule` nebo z něj odvozenou třídu. Další informace o Průvodce projektem ATL naleznete v článku [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md).  
  
 Kromě `CComModule`, knihovna ATL poskytuje [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), která implementuje modul objektu apartment modelu pro služby souborů exe a Windows. Odvození z modulu `CComAutoThreadModule` kdy budete chtít vytvořit objekty ve více objekty apartment.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [Catlmodule –](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CComModule`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="getclassobject"></a>  CComModule::GetClassObject  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HRESULT GetClassObject(  
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *rclsid*  
 [in] Identifikátor CLSID objektu, který má být vytvořen.  
  
 *riid*  
 [in] Identifikátor IID požadované rozhraní.  
  
 *ppv*  
 [out] Ukazatel na ukazatel rozhraní, který je identifikován *riid*. Pokud objekt nepodporuje toto rozhraní *ppv* nastaven na hodnotu NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří objekt zadaným identifikátorem CLSID a načte ukazatel rozhraní k tomuto objektu.  
  
 `GetClassObject` je k dispozici pouze na knihovny DLL.  
  
##  <a name="getmoduleinstance"></a>  CComModule::GetModuleInstance  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HINSTANCE GetModuleInstance() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 HINSTANCE identifikaci tohoto modulu.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí [m_hInst](#m_hinst) datový člen.  
  
##  <a name="getresourceinstance"></a>  CComModule::GetResourceInstance  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HINSTANCE GetResourceInstance() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 HINSTANCE.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí [m_hInstResource](#m_hinstresource) datový člen.  
  
##  <a name="gettypelibinstance"></a>  CComModule::GetTypeLibInstance  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HINSTANCE GetTypeLibInstance() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 HINSTANCE.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí [m_hInstTypeLib](#m_hinsttypelib) datový člen.  
  
##  <a name="init"></a>  V: CComModule::Init  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *p*  
 [in] Ukazatel na pole položek mapování objektu.  
  
 *h*  
 [in] Předány HINSTANCE `DLLMain` nebo `WinMain`.  
  
 *plibid*  
 [in] Ukazatel na LIBID knihovnu typů, který je přidružený k projektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje všechny datové členy.  
  
##  <a name="m_csobjmap"></a>  CComModule::m_csObjMap  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
CRITICAL_SECTION m_csObjMap;
```  
  
### <a name="remarks"></a>Poznámky  
 Zajišťuje synchronizované přístup k objektu map.  
  
##  <a name="m_cstypeinfoholder"></a>  CComModule::m_csTypeInfoHolder  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
CRITICAL_SECTION m_csTypeInfoHolder;
```  
  
### <a name="remarks"></a>Poznámky  
 Zajišťuje synchronizované přístup ke knihovně typů.  
  
##  <a name="m_cswindowcreate"></a>  CComModule::m_csWindowCreate  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
CRITICAL_SECTION m_csWindowCreate;
```  
  
### <a name="remarks"></a>Poznámky  
 Zajišťuje synchronizované přístup k informacím o třídě okna a statická data použít při vytváření okna.  
  
##  <a name="m_hinst"></a>  CComModule::m_hInst  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HINSTANCE m_hInst;
```  
  
### <a name="remarks"></a>Poznámky  
 Obsahuje popisovač instance modulu.  
  
 [Init](#init) metody nastaví `m_hInst` na popisovač předaný `DLLMain` nebo `WinMain`.  
  
##  <a name="m_hinstresource"></a>  CComModule::m_hInstResource  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HINSTANCE m_hInstResource;
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení obsahuje popisovač instance modulu.  
  
 [Init](#init) metody nastaví `m_hInstResource` na popisovač předaný `DLLMain` nebo `WinMain`. Můžete explicitně nastavit `m_hInstResource` na popisovač pro prostředek.  
  
 [GetResourceInstance](#getresourceinstance) metoda vrátí popisovač uložené v `m_hInstResource`.  
  
##  <a name="m_hinsttypelib"></a>  CComModule::m_hInstTypeLib  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HINSTANCE m_hInstTypeLib;
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení obsahuje popisovač instance modulu.  
  
 [Init](#init) metody nastaví `m_hInstTypeLib` na popisovač předaný `DLLMain` nebo `WinMain`. Můžete explicitně nastavit `m_hInstTypeLib` ke zpracování do knihovny typů.  
  
 [GetTypeLibInstance](#gettypelibinstance) metoda vrátí popisovač uložené v `m_hInstTypeLib`.  
  
##  <a name="m_pobjmap"></a>  CComModule::m_pObjMap  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```  
  
### <a name="remarks"></a>Poznámky  
 Odkazuje na objekt map udržuje instancí modulu.  
  
##  <a name="registerclasshelper"></a>  CComModule::RegisterClassHelper  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
ATL_DEPRECATED HRESULT RegisterClassHelper(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parametry  
 *identifikátor CLSID*  
 [in] Identifikátor CLSID objektu, který má být zaregistrován.  
  
 *lpszProgID*  
 [in] Identifikátor ProgID přidružená k objektu.  
  
 *lpszVerIndProgID*  
 [in] Identifikátor ProgID nezávislé na verzi přidružené k objektu.  
  
 *nDescID*  
 [in] Identifikátor prostředku řetězce pro popis objektu.  
  
 *dwFlags*  
 [in] Určuje model vláken k zadání v registru. Možné hodnoty jsou THREADFLAGS_APARTMENT, THREADFLAGS_BOTH nebo AUTPRXFLAG.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Zadá objektu standardní třídu registraci v registru systému.  
  
 [UpdateRegistryClass](#updateregistryclass) volání metody `RegisterClassHelper`.  
  
##  <a name="registerclassobjects"></a>  CComModule::RegisterClassObjects  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *dwClsContext*  
 [in] Určuje kontext, ve kterém má být spuštěn objektu třídy. Možné hodnoty jsou CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER nebo CLSCTX_LOCAL_SERVER. Popis těchto hodnot najdete v tématu [CLSCTX](https://msdn.microsoft.com/library/windows/desktop/ms693716) v sadě Windows SDK.  
  
 *dwFlags*  
 [in] Určuje typy připojení k objektu třídy. Možné hodnoty jsou REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE nebo REGCLS_MULTI_SEPARATE. Popis těchto hodnot najdete v tématu [REGCLS](/windows/desktop/api/combaseapi/ne-combaseapi-tagregcls) v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Zaregistruje objekt třídy EXE OLE, můžete k němu připojit další aplikace. Tato metoda je pouze možné souborů exe.  
  
##  <a name="registerserver"></a>  CComModule::RegisterServer  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,  
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *bRegTypeLib*  
 [in] Určuje, zda se zaregistruje knihovnu typů. Výchozí hodnota je FALSE.  
  
 *pCLSID*  
 [in] Odkazuje na identifikátor CLSID objekt, který má být zaregistrován. Pokud se zaregistruje NULL (výchozí hodnota), všechny objekty v mapě objektů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 V závislosti na tom *pCLSID* parametr, aktualizuje systémového registru pro jednu třídu objektu, nebo pro všechny objekty v mapě objektů.  
  
 Pokud *bRegTypeLib* má hodnotu TRUE, bude také aktualizovat informace knihovny typů.  
  
 Zobrazit [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) informace o tom, jak přidat položku do mapy objektu.  
  
 `RegisterServer` bude automaticky volána `DLLRegisterServer` pro knihovnu DLL nebo podle `WinMain` pro spuštění pomocí EXE `/RegServer` možnost příkazového řádku.  
  
##  <a name="registertypelib"></a>  CComModule::RegisterTypeLib  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *lpszIndex*  
 [in] Řetězec ve formátu `"\\N"`, kde `N` je celočíselný index prostředku knihovny typů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Přidá informace o knihovnu typů do systémového registru.  
  
 Pokud instance modulu obsahuje více knihoven typů, použijte k určení, které knihovna typů by měla sloužit druhou verzi této metody.  
  
##  <a name="revokeclassobjects"></a>  CComModule::RevokeClassObjects  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HRESULT RevokeClassObjects() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Odebere objekt třídy. Tato metoda je pouze možné souborů exe.  
  
##  <a name="term"></a>  Ccommodule::TERM.  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
void Term() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny datové členy.  
  
##  <a name="unregisterclasshelper"></a>  CComModule::UnregisterClassHelper  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
ATL_DEPRECATED HRESULT UnregisterClassHelper(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```  
  
### <a name="parameters"></a>Parametry  
 *identifikátor CLSID*  
 [in] Identifikátor CLSID objektu se zrušit registraci  
  
 *lpszProgID*  
 [in] Identifikátor ProgID přidružená k objektu.  
  
 *lpszVerIndProgID*  
 [in] Identifikátor ProgID nezávislé na verzi přidružené k objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Odebere registraci standardní třídu objektu ze systémového registru.  
  
 [UpdateRegistryClass](#updateregistryclass) volání metody `UnregisterClassHelper`.  
  
##  <a name="unregisterserver"></a>  CComModule::UnregisterServer  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```  
  
### <a name="parameters"></a>Parametry  
 *bUnRegTypeLib*  
 Při hodnotě TRUE je také zrušit registraci knihovny typů.  
  
 *pCLSID*  
 Odkazuje na identifikátor CLSID objekt, který má být zrušena registrace. Pokud hodnotu NULL (výchozí hodnota), všechny objekty v mapě objektů bude zrušena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 V závislosti na tom *pCLSID* parametr, zruší registraci jedné třídy objektu nebo všechny objekty v mapě objektů.  
  
 `UnregisterServer` bude automaticky volána `DLLUnregisterServer` pro knihovnu DLL nebo podle `WinMain` pro spuštění pomocí EXE `/UnregServer` možnost příkazového řádku.  
  
 Zobrazit [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) informace o tom, jak přidat položku do mapy objektu.  
  
##  <a name="updateregistryclass"></a>  CComModule::UpdateRegistryClass  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
ATL_DEPRECATED HRESULT UpdateRegistryClass(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags,
    BOOL bRegister);

ATL_DEPRECATED HRESULT UpdateRegistryClass(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    LPCTSTR szDesc,
    DWORD dwFlags,
    BOOL bRegister);
```  
  
### <a name="parameters"></a>Parametry  
 *identifikátor CLSID*  
 Identifikátor CLSID objektu, který má být zaregistrován nebo zrušení registrace  
  
 *lpszProgID*  
 Identifikátor ProgID přidružená k objektu.  
  
 *lpszVerIndProgID*  
 Identifikátor ProgID nezávislé na verzi přidružené k objektu.  
  
 *nDescID*  
 Identifikátor prostředku řetězců pro popis objektu.  
  
 *szDesc*  
 Řetězec obsahující popis objektu.  
  
 *dwFlags*  
 Určuje model vláken k zadání v registru. Možné hodnoty jsou THREADFLAGS_APARTMENT, THREADFLAGS_BOTH nebo AUTPRXFLAG.  
  
 *bRegister*  
 Určuje, zda by měly být zaregistrovány objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *bRegister* má hodnotu TRUE, tato metoda zadá objektu standardní třídu registraci v registru systému.  
  
 Pokud *bRegister* má hodnotu FALSE, odebere registraci objektu.  
  
 V závislosti na hodnotě z *bRegister*, `UpdateRegistryClass` zavolá buď [RegisterClassHelper](#registerclasshelper) nebo [UnregisterClassHelper](#unregisterclasshelper).  
  
 Zadáním [DECLARE_REGISTRY](registry-macros.md#declare_registry) – makro, `UpdateRegistryClass` bude vyvolán automaticky při zpracování vaší mapě objektů.  
  
##  <a name="updateregistryfromresourced"></a>  CComModule::UpdateRegistryFromResourceD  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
virtual HRESULT UpdateRegistryFromResourceD(  
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceD(  
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw ();
```  
  
### <a name="parameters"></a>Parametry  
 *lpszRes*  
 [in] Název prostředku.  
  
 *nResID*  
 [in] ID prostředku.  
  
 *bRegister*  
 [in] Určuje, zda by měly být zaregistrovány objektu.  
  
 *pMapEntries*  
 [in] Ukazatel na náhradní mapy ukládání hodnot, které jsou přidružené k nahraditelné parametry skriptu. ATL – automaticky použije `%MODULE%`. Pokud chcete používat další nahraditelné parametry, naleznete v poznámkách podrobnosti. Jinak použijte výchozí hodnotu NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Spustí skript obsažené v prostředku zadaného parametrem *lpszRes* nebo *nResID*.  
  
 Pokud *bRegister* má hodnotu TRUE, tato metoda registruje v systémovém registru objektu; v opačném případě ji zruší registraci objektu.  
  
 Zadáním [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) nebo [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) – makro, `UpdateRegistryFromResourceD` bude vyvolán automaticky při zpracování vaší mapě objektů.  
  
> [!NOTE]
>  Nahradit nahrazujícími hodnotami v době běhu, nezadávejte DECLARE_REGISTRY_RESOURCE nebo DECLARE_REGISTRY_RESOURCEID – makro. Místo toho vytvořte pole `_ATL_REGMAP_ENTRIES` struktur, kde každý záznam obsahuje zástupný symbol proměnné souřadnicí hodnotu nahraďte zástupný text v době běhu. Poté zavolejte `UpdateRegistryFromResourceD`, předání pole *pMapEntries* parametru. Tento postup přidá nahrazujícími hodnotami v `_ATL_REGMAP_ENTRIES` struktury do vašeho registrátora nahrazení mapy.  
  
> [!NOTE]
>  Staticky propojit komponenta knihovny ATL registru (Registrar), najdete v článku [UpdateRegistryFromResourceS](#updateregistryfromresources).  
  
 Další informace o nahraditelné parametry a skriptů, najdete v článku [The komponenta knihovny ATL registru (Registrar)](../../atl/atl-registry-component-registrar.md).  
  
##  <a name="updateregistryfromresources"></a>  CComModule::UpdateRegistryFromResourceS  
 Od verze ATL 7.0 `CComModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
virtual HRESULT UpdateRegistryFromResourceS(  
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceS(  
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *lpszRes*  
 [in] Název prostředku.  
  
 *nResID*  
 [in] ID prostředku.  
  
 *bRegister*  
 [in] Určuje, zda by měly být zaregistrovány skript prostředků.  
  
 *pMapEntries*  
 [in] Ukazatel na náhradní mapy ukládání hodnot, které jsou přidružené k nahraditelné parametry skriptu. ATL – automaticky použije `%MODULE%`. Pokud chcete používat další nahraditelné parametry, naleznete v poznámkách podrobnosti. Jinak použijte výchozí hodnotu NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Podobně jako [UpdateRegistryFromResourceD](#updateregistryfromresourced) s výjimkou `UpdateRegistryFromResourceS` vytvoří statický odkaz na komponentu ATL registru (Registrar).  
  
 `UpdateRegistryFromResourceS` bude vyvolána automaticky při zpracování vaší mapě objektů, pokud přidáte `#define _ATL_STATIC_REGISTRY` do vaší stdafx.h.  
  
> [!NOTE]
>  Nahradit nahrazujícími hodnotami v době běhu, nezadávejte [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) nebo [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) – makro. Místo toho vytvořte pole `_ATL_REGMAP_ENTRIES` struktur, kde každý záznam obsahuje zástupný symbol proměnné souřadnicí hodnotu nahraďte zástupný text v době běhu. Poté zavolejte `UpdateRegistryFromResourceS`, předání pole *pMapEntries* parametru. Tento postup přidá nahrazujícími hodnotami v `_ATL_REGMAP_ENTRIES` struktury do vašeho registrátora nahrazení mapy.  
  
 Další informace o nahraditelné parametry a skriptů, najdete v článku [The komponenta knihovny ATL registru (Registrar)](../../atl/atl-registry-component-registrar.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled tříd](../../atl/atl-class-overview.md)
