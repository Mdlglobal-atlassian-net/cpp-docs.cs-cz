---
title: CComModule – třída | Microsoft Docs
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
ms.openlocfilehash: 05b4ec763f6ee719e96627be3dc81a1e9b56c2c1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ccommodule-class"></a>CComModule – třída
Od verze ATL 7.0 `CComModule` je zastaralý: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComModule : public _ATL_MODULE
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComModule::GetClassObject](#getclassobject)|Vytvoří objekt zadaného CLSID. Pro knihovny DLL pouze.|  
|[CComModule::GetModuleInstance](#getmoduleinstance)|Vrátí `m_hInst`.|  
|[CComModule::GetResourceInstance](#getresourceinstance)|Vrátí `m_hInstResource`.|  
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|Vrátí `m_hInstTypeLib`.|  
|[CComModule::Init](#init)|Inicializuje datových členů.|  
|[CComModule::RegisterClassHelper](#registerclasshelper)|Zadá registrace standardní třídy objektu v registru systému.|  
|[CComModule::RegisterClassObjects](#registerclassobjects)|Zaregistruje třídu objektu. Pro pouze souborů exe.|  
|[CComModule::RegisterServer](#registerserver)|Aktualizuje registr systému pro každý objekt v mapování objektu.|  
|[CComModule::RegisterTypeLib](#registertypelib)|Zaregistruje knihovnu typů.|  
|[CComModule::RevokeClassObjects](#revokeclassobjects)|Odvolá objektu třídy. Pro pouze souborů exe.|  
|[CComModule::Term](#term)|Uvolní datových členů.|  
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|Odebere registraci standardní třídu objektu z registru systému.|  
|[CComModule::UnregisterServer](#unregisterserver)|Zruší registraci každý objekt v mapování objektu.|  
|[CComModule::UpdateRegistryClass](#updateregistryclass)|Zaregistruje nebo zrušení registrace registrace standardní třídy objektu.|  
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Spustí skript obsažené v zadaný prostředek k registraci nebo zrušení registrace objektu.|  
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Staticky odkazuje na komponentu ATL registru. Spustí skript obsažené v zadaný prostředek k registraci nebo zrušení registrace objektu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComModule::m_csObjMap](#m_csobjmap)|Zajišťuje synchronizované přístup k informacím mapu objektu.|  
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|Zajišťuje synchronizované přístup k informacím knihovny typu.|  
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|Zajišťuje synchronizované přístup k informacím třída okno a statických dat použít během vytváření okna.|  
|[CComModule::m_hInst](#m_hinst)|Obsahuje popisovač instancí modulu.|  
|[CComModule::m_hInstResource](#m_hinstresource)|Ve výchozím nastavení obsahuje popisovač instancí modulu.|  
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|Ve výchozím nastavení obsahuje popisovač instancí modulu.|  
|[CComModule::m_pObjMap](#m_pobjmap)|Odkazuje na objekt mapy udržované instancí modulu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato třída je zastaralá a průvodců generování kódu ATL teď použít [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) a [CAtlModule](../../atl/reference/catlmodule-class.md) odvozených třídách. V tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) Další informace. Informace, které následuje je pro použití s aplikacemi, které jsou vytvořené pomocí starší verze ATL. `CComModule` je stále součástí knihovny ATL pro zpětné schopnosti.  
  
 `CComModule` implementuje modul server COM, umožňuje klientům přístup k součástem modulu. `CComModule` podporuje knihovny DLL (v procesu) a moduly EXE (místní).  
  
 A `CComModule` instance používá mapování objektu udržovat sadu – třída definice objektu. Tato mapa objektu je implementovaný jako pole `_ATL_OBJMAP_ENTRY` struktury a obsahuje informace pro:  
  
-   Zadávání a odebírání popisy objektů v registru systému.  
  
-   Vytváření instancí objektů prostřednictvím objekt pro vytváření tříd.  
  
-   V komponentě navazování komunikace mezi klientem a kořenový objekt.  
  
-   Provádí správu životního cyklu objektů tříd.  
  
 Když spustíte objekty knihovny ATL COM AppWizard, průvodce automaticky vygeneruje `_Module`, globální instanci `CComModule` nebo z něj odvozenou třídu. Další informace o Průvodci projektu knihovny ATL, najdete v článku [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md).  
  
 Kromě `CComModule`, poskytuje ATL [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), která implementuje modul apartment model služeb souborů exe a systému Windows. Odvození modul z `CComAutoThreadModule` když chcete vytvořit objekty v několika Apartment.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CComModule`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="getclassobject"></a>  CComModule::GetClassObject  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HRESULT GetClassObject(  
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rclsid`  
 [v] CLSID objektu, který se má vytvořit.  
  
 `riid`  
 [v] Identifikátory IID požadované rozhraní.  
  
 `ppv`  
 [out] Ukazatel na ukazatel rozhraní identifikovaný `riid`. Pokud objekt nepodporuje toto rozhraní `ppv` je nastaven na **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří objekt zadaného CLSID a načte ukazatele rozhraní k tomuto objektu.  
  
 `GetClassObject` je k dispozici pouze knihovny DLL.  
  
##  <a name="getmoduleinstance"></a>  CComModule::GetModuleInstance  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HINSTANCE GetModuleInstance() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `HINSTANCE` Identifikující tento modul.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí [m_hInst](#m_hinst) – datový člen.  
  
##  <a name="getresourceinstance"></a>  CComModule::GetResourceInstance  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HINSTANCE GetResourceInstance() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `HINSTANCE`.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí [m_hInstResource](#m_hinstresource) – datový člen.  
  
##  <a name="gettypelibinstance"></a>  CComModule::GetTypeLibInstance  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HINSTANCE GetTypeLibInstance() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `HINSTANCE`.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí [m_hInstTypeLib](#m_hinsttypelib) – datový člen.  
  
##  <a name="init"></a>  CComModule::Init  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 [v] Ukazatel na pole položek mapování objektu.  
  
 `h`  
 [v] `HINSTANCE` Předaný **DLLMain** nebo `WinMain`.  
  
 `plibid`  
 [v] Ukazatel na ID KNIHOVNY knihovny typů, který je přidružený k projektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje všechny datové členy.  
  
##  <a name="m_csobjmap"></a>  CComModule::m_csObjMap  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
CRITICAL_SECTION m_csObjMap;
```  
  
### <a name="remarks"></a>Poznámky  
 Zajišťuje synchronizované přístup k mapování objektu.  
  
##  <a name="m_cstypeinfoholder"></a>  CComModule::m_csTypeInfoHolder  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
CRITICAL_SECTION m_csTypeInfoHolder;
```  
  
### <a name="remarks"></a>Poznámky  
 Zajišťuje synchronizované přístup ke knihovně typů.  
  
##  <a name="m_cswindowcreate"></a>  CComModule::m_csWindowCreate  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
CRITICAL_SECTION m_csWindowCreate;
```  
  
### <a name="remarks"></a>Poznámky  
 Zajišťuje synchronizované přístup k okno informace o třídě a statických dat použít během vytváření okna.  
  
##  <a name="m_hinst"></a>  CComModule::m_hInst  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HINSTANCE m_hInst;
```  
  
### <a name="remarks"></a>Poznámky  
 Obsahuje popisovač instancí modulu.  
  
 [Init](#init) metoda nastaví `m_hInst` na popisovač předaný **DLLMain** nebo `WinMain`.  
  
##  <a name="m_hinstresource"></a>  CComModule::m_hInstResource  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HINSTANCE m_hInstResource;
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení obsahuje popisovač instancí modulu.  
  
 [Init](#init) metoda nastaví `m_hInstResource` na popisovač předaný **DLLMain** nebo `WinMain`. Je možné nastavit explicitně `m_hInstResource` na popisovač pro prostředek.  
  
 [GetResourceInstance](#getresourceinstance) metoda vrátí popisovač uložené v `m_hInstResource`.  
  
##  <a name="m_hinsttypelib"></a>  CComModule::m_hInstTypeLib  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HINSTANCE m_hInstTypeLib;
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení obsahuje popisovač instancí modulu.  
  
 [Init](#init) metoda nastaví `m_hInstTypeLib` na popisovač předaný **DLLMain** nebo `WinMain`. Je možné nastavit explicitně `m_hInstTypeLib` na popisovač knihovny typů.  
  
 [GetTypeLibInstance](#gettypelibinstance) metoda vrátí popisovač uložené v `m_hInstTypeLib`.  
  
##  <a name="m_pobjmap"></a>  CComModule::m_pObjMap  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```  
  
### <a name="remarks"></a>Poznámky  
 Odkazuje na objekt mapy udržované instancí modulu.  
  
##  <a name="registerclasshelper"></a>  CComModule::RegisterClassHelper  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
ATL_DEPRECATED HRESULT RegisterClassHelper(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 [v] CLSID objektu k registraci.  
  
 `lpszProgID`  
 [v] ProgID přidružená k objektu.  
  
 `lpszVerIndProgID`  
 [v] ProgID nezávislé na verzi, přidružený k objektu.  
  
 `nDescID`  
 [v] Identifikátor řetězec prostředku pro popis objektu.  
  
 `dwFlags`  
 [v] Určuje model vláken zadat v registru. Možné hodnoty jsou **THREADFLAGS_APARTMENT**, **THREADFLAGS_BOTH**, nebo **AUTPRXFLAG**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Zadá registrace standardní třídy objektu v registru systému.  
  
 [UpdateRegistryClass](#updateregistryclass) volání metod `RegisterClassHelper`.  
  
##  <a name="registerclassobjects"></a>  CComModule::RegisterClassObjects  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwClsContext`  
 [v] Určuje kontext, ve kterém má být spuštěna objektu třídy. Možné hodnoty jsou **CLSCTX_INPROC_SERVER**, **CLSCTX_INPROC_HANDLER**, nebo **CLSCTX_LOCAL_SERVER**. Popis těchto hodnot najdete v tématu [CLSCTX](http://msdn.microsoft.com/library/windows/desktop/ms693716) ve Windows SDK.  
  
 `dwFlags`  
 [v] Určuje typy připojení k objektu třídy. Možné hodnoty jsou **REGCLS_SINGLEUSE**, **REGCLS_MULTIPLEUSE**, nebo **REGCLS_MULTI_SEPARATE**. Popis těchto hodnot najdete v tématu [REGCLS](http://msdn.microsoft.com/library/windows/desktop/ms679697) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Zaregistruje objekt EXE – třída se OLE, takže k nim mohla připojit jiné aplikace. Tato metoda je pouze k dispozici pro souborů exe.  
  
##  <a name="registerserver"></a>  CComModule::RegisterServer  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,  
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bRegTypeLib`  
 [v] Určuje, zda bude zaregistrována knihovny typů. Výchozí hodnota je **FALSE**.  
  
 `pCLSID`  
 [v] Body CLSID objekt, který má být zaregistrován. Pokud **NULL** (výchozí hodnota), všechny objekty v mapování objektu bude zaregistrována.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 V závislosti na tom `pCLSID` parametr aktualizuje registr systému pro jednu třídu objektu, nebo pro všechny objekty v mapování objektu.  
  
 Pokud `bRegTypeLib` je **TRUE**, informace typu knihovny se také zaktualizují.  
  
 V tématu [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) informace o tom, jak přidat položku do mapování objektu.  
  
 `RegisterServer` bude volána automaticky **DLLRegisterServer** pro knihovny DLL nebo pomocí `WinMain` pro EXE spustit s **/regserver** možnost příkazového řádku.  
  
##  <a name="registertypelib"></a>  CComModule::RegisterTypeLib  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszIndex`  
 [v] Řetězec ve formátu `"\\N"`, kde `N` je celé číslo indexu TYPELIB prostředku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Informace o typu knihovny se přidá do registru systému.  
  
 Pokud instance modul obsahuje více knihovny typů, použijte k určení, které knihovny typů by měl používat druhá verze této metody.  
  
##  <a name="revokeclassobjects"></a>  CComModule::RevokeClassObjects  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HRESULT RevokeClassObjects() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Odebere objekt třídy. Tato metoda je pouze k dispozici pro souborů exe.  
  
##  <a name="term"></a>  CComModule::Term  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
void Term() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny datové členy.  
  
##  <a name="unregisterclasshelper"></a>  CComModule::UnregisterClassHelper  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
ATL_DEPRECATED HRESULT UnregisterClassHelper(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 [v] CLSID objektu se zrušit registraci.  
  
 `lpszProgID`  
 [v] ProgID přidružená k objektu.  
  
 `lpszVerIndProgID`  
 [v] ProgID nezávislé na verzi, přidružený k objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Odebere registraci standardní třídu objektu z registru systému.  
  
 [UpdateRegistryClass](#updateregistryclass) volání metod `UnregisterClassHelper`.  
  
##  <a name="unregisterserver"></a>  CComModule::UnregisterServer  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```  
  
### <a name="parameters"></a>Parametry  
 `bUnRegTypeLib`  
 Pokud **TRUE**, je také zrušit registraci knihovny typů.  
  
 `pCLSID`  
 Body CLSID objekt, který má neregistrované. Pokud **NULL** (výchozí hodnota), všechny objekty v mapování objektu bude zrušena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 V závislosti na tom `pCLSID` parametr zruší registraci objekt jednu třídu nebo všechny objekty v mapování objektu.  
  
 `UnregisterServer` bude volána automaticky **DLLUnregisterServer** pro knihovny DLL nebo pomocí `WinMain` pro EXE spustit s **/Unregserver** možnost příkazového řádku.  
  
 V tématu [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) informace o tom, jak přidat položku do mapování objektu.  
  
##  <a name="updateregistryclass"></a>  CComModule::UpdateRegistryClass  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
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
 `clsid`  
 Identifikátor CLSID objekt, který má být zaregistrován nebo zrušit její registraci.  
  
 `lpszProgID`  
 ProgID přidružená k objektu.  
  
 `lpszVerIndProgID`  
 ProgID nezávislé na verzi, přidružený k objektu.  
  
 `nDescID`  
 Identifikátor řetězec prostředku pro popis objektu.  
  
 `szDesc`  
 Řetězec obsahující popis objektu.  
  
 `dwFlags`  
 Určuje model vláken zadat v registru. Možné hodnoty jsou **THREADFLAGS_APARTMENT**, **THREADFLAGS_BOTH**, nebo **AUTPRXFLAG**.  
  
 `bRegister`  
 Označuje, zda by měl být registrován objekt.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `bRegister` je **TRUE**, tato metoda zadá registrace standardní třídy objektu v registru systému.  
  
 Pokud `bRegister` je **FALSE**, se odeberou registrace objektu.  
  
 V závislosti na hodnotě `bRegister`, `UpdateRegistryClass` zavolá buď [RegisterClassHelper](#registerclasshelper) nebo [UnregisterClassHelper](#unregisterclasshelper).  
  
 Zadáním [DECLARE_REGISTRY](registry-macros.md#declare_registry) makro, `UpdateRegistryClass` , který bude vyvolán automaticky při zpracování vaší mapování objektu.  
  
##  <a name="updateregistryfromresourced"></a>  CComModule::UpdateRegistryFromResourceD  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
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
 `lpszRes`  
 [v] Název prostředku.  
  
 `nResID`  
 [v] ID prostředku.  
  
 `bRegister`  
 [v] Označuje, zda by měl být registrován objekt.  
  
 `pMapEntries`  
 [v] Ukazatel na mapě nahrazení ukládání hodnot přidružený ke skriptu nahraditelné parametry. Automaticky použije ATL `%MODULE%`. Pokud chcete používat další nahraditelné parametry, najdete v části poznámky podrobnosti. Jinak použijte **NULL** výchozí hodnota.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Spustí skript obsažené v prostředku zadaného parametrem `lpszRes` nebo `nResID`.  
  
 Pokud `bRegister` je **TRUE**, tato metoda registruje objekt v registru systému; jinak, zruší registraci objektu.  
  
 Zadáním [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) nebo [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) makro, `UpdateRegistryFromResourceD` , který bude vyvolán automaticky při zpracování vaší mapování objektu.  
  
> [!NOTE]
>  Pokud chcete nahradit nahrazení hodnoty v době běhu, nezadávejte `DECLARE_REGISTRY_RESOURCE` nebo `DECLARE_REGISTRY_RESOURCEID` makro. Místo toho vytvořte pole **_ATL_REGMAP_ENTRIES** struktury, kde každý záznam obsahuje zástupný symbol proměnné spárovat s hodnotou pro nahraďte zástupný symbol v době běhu. Potom zavolejte `UpdateRegistryFromResourceD`, probíhá předání pole `pMapEntries` parametr. Tento postup přidá všechny hodnoty nahrazení ve **_ATL_REGMAP_ENTRIES** struktury vašeho registrátora nahrazení mapu.  
  
> [!NOTE]
>  Staticky odkaz na komponentu ATL registru (Registrar), najdete v tématu [UpdateRegistryFromResourceS](#updateregistryfromresources).  
  
 Další informace o nahraditelné parametry a skriptování, najdete v článku [ATL komponenta registru (Registrar)](../../atl/atl-registry-component-registrar.md).  
  
##  <a name="updateregistryfromresources"></a>  CComModule::UpdateRegistryFromResourceS  
 Od verze ATL 7.0 `CComModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
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
 `lpszRes`  
 [v] Název prostředku.  
  
 `nResID`  
 [v] ID prostředku.  
  
 `bRegister`  
 [v] Určuje, jestli by měl být zaregistrované skriptu prostředků.  
  
 `pMapEntries`  
 [v] Ukazatel na mapě nahrazení ukládání hodnot přidružený ke skriptu nahraditelné parametry. Automaticky použije ATL `%MODULE%`. Pokud chcete používat další nahraditelné parametry, najdete v části poznámky podrobnosti. Jinak použijte **NULL** výchozí hodnota.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Podobně jako [UpdateRegistryFromResourceD](#updateregistryfromresourced) s výjimkou `UpdateRegistryFromResourceS` vytvoří statický odkaz na komponentu ATL registru (Registrar).  
  
 `UpdateRegistryFromResourceS` bude volána automaticky při zpracování vaší mapování objektu zadaný přidáte `#define _ATL_STATIC_REGISTRY` do vaší stdafx.h.  
  
> [!NOTE]
>  Pokud chcete nahradit nahrazení hodnoty v době běhu, nezadávejte [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) nebo [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) makro. Místo toho vytvořte pole **_ATL_REGMAP_ENTRIES** struktury, kde každý záznam obsahuje zástupný symbol proměnné spárovat s hodnotou pro nahraďte zástupný symbol v době běhu. Potom zavolejte `UpdateRegistryFromResourceS`, probíhá předání pole `pMapEntries` parametr. Tento postup přidá všechny hodnoty nahrazení ve **_ATL_REGMAP_ENTRIES** struktury vašeho registrátora nahrazení mapu.  
  
 Další informace o nahraditelné parametry a skriptování, najdete v článku [ATL komponenta registru (Registrar)](../../atl/atl-registry-component-registrar.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
