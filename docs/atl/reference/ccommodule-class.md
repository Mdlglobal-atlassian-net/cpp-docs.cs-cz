---
title: CComModule – třída
ms.date: 08/19/2019
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
helpviewer_keywords:
- CComModule class
- DLL modules [C++], ATL
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
ms.openlocfilehash: 5e30f847ff99a80ab19b880728472a339fd4cbe5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747929"
---
# <a name="ccommodule-class"></a>CComModule – třída

Od ATL 7.0, `CComModule` je zastaralé: viz [třídy modulu ATL](../../atl/atl-module-classes.md) další podrobnosti.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComModule::GetClassObject](#getclassobject)|Vytvoří objekt zadaného identifikátoru CLSID. Pouze pro knihovny DLL.|
|[CcomModule::GetModuleInstance](#getmoduleinstance)|Vrací objekt `m_hInst`.|
|[CComModule::GetResourceInstance](#getresourceinstance)|Vrací objekt `m_hInstResource`.|
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|Vrací objekt `m_hInstTypeLib`.|
|[CComModule::Init](#init)|Inicializuje datové členy.|
|[CComModule::RegisterClassHelper](#registerclasshelper)|Zadá registraci standardní třídy objektu do systémového registru.|
|[CComModule::RegisterClassObjects](#registerclassobjects)|Registruje objekt třídy. Pouze pro EXEs.|
|[CComModule::RegisterServer](#registerserver)|Aktualizuje systémový registr pro každý objekt v mapě objektů.|
|[CComModule::RegisterTypeLib](#registertypelib)|Zaregistruje knihovnu typů.|
|[CComModule::RevokeClassObjects](#revokeclassobjects)|Odvolá objekt třídy. Pouze pro EXEs.|
|[CComModule::Termín](#term)|Uvolní datové členy.|
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|Odebere registraci standardní třídy objektu ze systémového registru.|
|[CComModule::Zrušit registraciserveru](#unregisterserver)|Zruší registrace každého objektu v mapě objektů.|
|[CComModule::UpdateRegistryClass](#updateregistryclass)|Zaregistruje nebo zruší registrace standardní třídy objektu.|
|[Ccommodule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Spustí skript obsažený v zadaném prostředku k registraci nebo zrušení registrace objektu.|
|[Ccommodule::UpdateRegistryFromResources](#updateregistryfromresources)|Staticky odkazuje na součást registru ATL. Spustí skript obsažený v zadaném prostředku k registraci nebo zrušení registrace objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComModule::m_csObjMap](#m_csobjmap)|Zajišťuje synchronizovaný přístup k informacím o mapě objektů.|
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|Zajišťuje synchronizovaný přístup k informacím knihovny typů.|
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|Zajišťuje synchronizovaný přístup k informacím o třídě okna a statickým datům používaným při vytváření okna.|
|[CComModule::m_hInst](#m_hinst)|Obsahuje popisovač instance modulu.|
|[CComModule::m_hInstResource](#m_hinstresource)|Ve výchozím nastavení obsahuje popisovač instance modulu.|
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|Ve výchozím nastavení obsahuje popisovač instance modulu.|
|[CComModule::m_pObjMap](#m_pobjmap)|Odkazuje na mapu objektů udržovanou instancí modulu.|

## <a name="remarks"></a>Poznámky

> [!NOTE]
> Tato třída je zastaralá a průvodci generování kódu ATL nyní používají odvozené třídy [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) a [CAtlModule.](../../atl/reference/catlmodule-class.md) Další informace naleznete [v tématu Třídy modulu ATL.](../../atl/atl-module-classes.md) Následující informace jsou určeny pro použití s aplikacemi vytvořenými se staršími verzemi atl. `CComModule`je stále součástí atl pro zpětně schopnosti.

`CComModule`implementuje serverový modul COM, který umožňuje klientovi přístup ke komponentám modulu. `CComModule`podporuje moduly DLL (in-process) i EXE (local).

Instance `CComModule` používá mapu objektů k zachování sady definic objektů třídy. Tato mapa objektů je implementována jako pole `_ATL_OBJMAP_ENTRY` struktur a obsahuje informace pro:

- Zadání a odebrání popisů objektů v systémovém registru.

- Vytváření vytváření instancí objektů prostřednictvím třídy factory.

- Navazování komunikace mezi klientem a kořenovým objektem v komponentě.

- Provádění správy životnosti objektů třídy.

Při spuštění průvodce atl COM AppWizard průvodce `_Module`automaticky generuje `CComModule` , globální instance nebo třídy odvozené z něj. Další informace o Průvodci projektem atl naleznete v článku [Vytvoření projektu atl](../../atl/reference/creating-an-atl-project.md).

Kromě `CComModule`, ATL poskytuje [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), který implementuje modul apartment-model pro EXEs a windows služby. Odvodit `CComAutoThreadModule` modul z, když chcete vytvořit objekty ve více bytech.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[Modul CAtl](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="ccommodulegetclassobject"></a><a name="getclassobject"></a>CComModule::GetClassObject

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parametry

*rclsid (rclsid)*<br/>
[v] CLSID objektu, který má být vytvořen.

*riid řekl:*<br/>
[v] IID požadovanérozhraní.

*Ppv*<br/>
[out] Ukazatel rozhraní určený *riid*. Pokud objekt nepodporuje toto rozhraní, *je hodnota ppv* nastavena na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Vytvoří objekt zadaného identifikátoru CLSID a načte k tomuto objektu ukazatel rozhraní.

`GetClassObject`je k dispozici pouze pro knihovny DLL.

## <a name="ccommodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CcomModule::GetModuleInstance

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Návratová hodnota

HINSTANCE identifikující tento modul.

### <a name="remarks"></a>Poznámky

Vrátí [datový člen m_hInst.](#m_hinst)

## <a name="ccommodulegetresourceinstance"></a><a name="getresourceinstance"></a>CComModule::GetResourceInstance

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Návratová hodnota

An HINSTANCE.

### <a name="remarks"></a>Poznámky

Vrátí datový člen [m_hInstResource.](#m_hinstresource)

## <a name="ccommodulegettypelibinstance"></a><a name="gettypelibinstance"></a>CComModule::GetTypeLibInstance

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>Návratová hodnota

An HINSTANCE.

### <a name="remarks"></a>Poznámky

Vrátí datový člen [m_hInstTypeLib.](#m_hinsttypelib)

## <a name="ccommoduleinit"></a><a name="init"></a>CComModule::Init

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
[v] Ukazatel na pole položek mapy objektů.

*H*<br/>
[v] HINSTANCE předánnebo `DLLMain` `WinMain`.

*plibid*<br/>
[v] Ukazatel na LIBID knihovny typů přidružené k projektu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Inicializuje všechny datové členy.

## <a name="ccommodulem_csobjmap"></a><a name="m_csobjmap"></a>CComModule::m_csObjMap

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>Poznámky

Zajišťuje synchronizovaný přístup k mapě objektů.

## <a name="ccommodulem_cstypeinfoholder"></a><a name="m_cstypeinfoholder"></a>CComModule::m_csTypeInfoHolder

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>Poznámky

Zajišťuje synchronizovaný přístup ke knihovně typů.

## <a name="ccommodulem_cswindowcreate"></a><a name="m_cswindowcreate"></a>CComModule::m_csWindowCreate

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>Poznámky

Zajišťuje synchronizovaný přístup k informacím o třídě okna a ke statickým datům používaným při vytváření oken.

## <a name="ccommodulem_hinst"></a><a name="m_hinst"></a>CComModule::m_hInst

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>Poznámky

Obsahuje popisovač instance modulu.

[Init](#init) metoda `m_hInst` nastaví popisovač `DLLMain` `WinMain`předán nebo .

## <a name="ccommodulem_hinstresource"></a><a name="m_hinstresource"></a>CComModule::m_hInstResource

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení obsahuje popisovač instance modulu.

[Init](#init) metoda `m_hInstResource` nastaví popisovač `DLLMain` `WinMain`předán nebo . Můžete explicitně `m_hInstResource` nastavit popisovač na prostředek.

Metoda [GetResourceInstance](#getresourceinstance) vrátí popisovač `m_hInstResource`uložený v aplikaci .

## <a name="ccommodulem_hinsttypelib"></a><a name="m_hinsttypelib"></a>CComModule::m_hInstTypeLib

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení obsahuje popisovač instance modulu.

[Init](#init) metoda `m_hInstTypeLib` nastaví popisovač `DLLMain` `WinMain`předán nebo . Můžete explicitně `m_hInstTypeLib` nastavit popisovač knihovny typů.

Metoda [GetTypeLibInstance](#gettypelibinstance) vrátí popisovač `m_hInstTypeLib`uložený v aplikaci .

## <a name="ccommodulem_pobjmap"></a><a name="m_pobjmap"></a>CComModule::m_pObjMap

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>Poznámky

Odkazuje na mapu objektů udržovanou instancí modulu.

## <a name="ccommoduleregisterclasshelper"></a><a name="registerclasshelper"></a>CComModule::RegisterClassHelper

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
ATL_DEPRECATED HRESULT RegisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*Identifikátor clsid*<br/>
[v] IDENTIFIKÁTOR CLSID objektu, který má být registrován.

*lpszProgID*<br/>
[v] ProgID přidružené k objektu.

*lpszVerIndProgID*<br/>
[v] ProgID nezávislé na verzi přidružené k objektu.

*nDescID*<br/>
[v] Identifikátor prostředků řetězce pro popis objektu.

*dwFlags*<br/>
[v] Určuje model zřetězení, který má být zadáván do registru. Možné hodnoty jsou THREADFLAGS_APARTMENT, THREADFLAGS_BOTH nebo AUTPRXFLAG.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Zadá registraci standardní třídy objektu do systémového registru.

Volání metody [UpdateRegistryClass](#updateregistryclass) `RegisterClassHelper`.

## <a name="ccommoduleregisterclassobjects"></a><a name="registerclassobjects"></a>CComModule::RegisterClassObjects

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parametry

*dwClsKontext*<br/>
[v] Určuje kontext, ve kterém má být objekt třídy spuštěn. Možné hodnoty jsou CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER nebo CLSCTX_LOCAL_SERVER. Popis těchto hodnot naleznete v části [CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) v sadě Windows SDK.

*dwFlags*<br/>
[v] Určuje typy připojení k objektu třídy. Možné hodnoty jsou REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE nebo REGCLS_MULTI_SEPARATE. Popis těchto hodnot naleznete v tématu [REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Zaregistruje objekt třídy EXE pomocí technologie OLE, aby se k němu mohly připojit jiné aplikace. Tato metoda je k dispozici pouze exes.

## <a name="ccommoduleregisterserver"></a><a name="registerserver"></a>CComModule::RegisterServer

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
[v] Označuje, zda bude knihovna typů registrována. Výchozí hodnota je FALSE.

*pCLSID*<br/>
[v] Odkazuje na CLSID objektu, který má být registrován. Pokud null (výchozí hodnota), budou zaregistrovány všechny objekty v mapě objektů.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

V závislosti na parametru *pCLSID* aktualizuje systémový registr pro jeden objekt třídy nebo pro všechny objekty v mapě objektů.

Pokud je *hodnota bRegTypeLib* PRAVDA, budou aktualizovány také informace knihovny typů.

Informace o přidání položky do mapy objektů naleznete v [OBJECT_ENTRY_AUTO.](object-map-macros.md#object_entry_auto)

`RegisterServer`bude volána `DLLRegisterServer` automaticky pro DLL `WinMain` nebo pro exe `/RegServer` spustit s možností příkazového řádku.

## <a name="ccommoduleregistertypelib"></a><a name="registertypelib"></a>CComModule::RegisterTypeLib

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
[v] Řetězec ve `"\\N"`formátu `N` , kde je index celéčíslo prostředku TYPELIB.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Přidá informace o knihovně typů do systémového registru.

Pokud instance modulu obsahuje více knihoven typů, použijte druhou verzi této metody k určení, která knihovna typů má být použita.

## <a name="ccommodulerevokeclassobjects"></a><a name="revokeclassobjects"></a>CComModule::RevokeClassObjects

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Odebere objekt třídy. Tato metoda je k dispozici pouze exes.

## <a name="ccommoduleterm"></a><a name="term"></a>CComModule::Termín

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```cpp
void Term() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny datové členy.

## <a name="ccommoduleunregisterclasshelper"></a><a name="unregisterclasshelper"></a>CComModule::UnregisterClassHelper

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>Parametry

*Identifikátor clsid*<br/>
[v] IDENTIFIKÁTOR CLSID objektu, který má být neregistrován.

*lpszProgID*<br/>
[v] ProgID přidružené k objektu.

*lpszVerIndProgID*<br/>
[v] ProgID nezávislé na verzi přidružené k objektu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Odebere registraci standardní třídy objektu ze systémového registru.

Volání metody [UpdateRegistryClass](#updateregistryclass) `UnregisterClassHelper`.

## <a name="ccommoduleunregisterserver"></a><a name="unregisterserver"></a>CComModule::Zrušit registraciserveru

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>Parametry

*bUnRegTypeLib*<br/>
Pokud true, knihovna typů je také neregistrována.

*pCLSID*<br/>
Odkazuje na CLSID objektu, který má být neregistrován. Pokud null (výchozí hodnota), všechny objekty v mapě objektu budou unregistered.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

V závislosti na parametru *pCLSID* zruší registrace buď jeden objekt třídy, nebo všechny objekty v mapě objektů.

`UnregisterServer`bude volána `DLLUnregisterServer` automaticky pro DLL `WinMain` nebo pro exe `/UnregServer` spustit s možností příkazového řádku.

Informace o přidání položky do mapy objektů naleznete v [OBJECT_ENTRY_AUTO.](object-map-macros.md#object_entry_auto)

## <a name="ccommoduleupdateregistryclass"></a><a name="updateregistryclass"></a>CComModule::UpdateRegistryClass

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

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

*Identifikátor clsid*<br/>
IDENTIFIKÁTOR CLSID objektu, který má být registrován nebo neregistrován.

*lpszProgID*<br/>
ProgID přidružené k objektu.

*lpszVerIndProgID*<br/>
ProgID nezávislé na verzi přidružené k objektu.

*nDescID*<br/>
Identifikátor prostředku řetězce pro popis objektu.

*szDesc*<br/>
Řetězec obsahující popis objektu.

*dwFlags*<br/>
Určuje model zřetězení, který má být zadáván do registru. Možné hodnoty jsou THREADFLAGS_APARTMENT, THREADFLAGS_BOTH nebo AUTPRXFLAG.

*bRegistrovat*<br/>
Označuje, zda má být objekt registrován.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pokud *bRegister* je PRAVDA, tato metoda zadá registraci standardní třídy objektu v systémovém registru.

Pokud *bRegister* je FALSE, odebere registraci objektu.

V závislosti na hodnotě `UpdateRegistryClass` *bRegister*volá [buď RegisterClassHelper](#registerclasshelper) nebo [UnregisterClassHelper](#unregisterclasshelper).

Zadáním [DECLARE_REGISTRY](registry-macros.md#declare_registry) makro, `UpdateRegistryClass` bude vyvolána automaticky při zpracování mapy objektu.

## <a name="ccommoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a>Ccommodule::UpdateRegistryFromResourceD

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

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

*lpszRes*<br/>
[v] Název prostředku.

*nResID*<br/>
[v] ID prostředku.

*bRegistrovat*<br/>
[v] Označuje, zda má být objekt registrován.

*pMapEntries*<br/>
[v] Ukazatel na náhradní mapu ukládající hodnoty přidružené k nahraditelným parametrům skriptu. Atl automaticky `%MODULE%`používá . Chcete-li použít další nahraditelné parametry, naleznete podrobnosti v části Poznámky. V opačném případě použijte výchozí hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Spustí skript obsažený v prostředku určeném *lpszRes* nebo *nResID*.

Pokud *bRegister* je PRAVDA, tato metoda zaregistruje objekt v systémovém registru; v opačném případě zruší registraci objektu.

Zadáním [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) nebo [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) `UpdateRegistryFromResourceD` makro, bude vyvolána automaticky při zpracování mapy objektu.

> [!NOTE]
> Chcete-li nahradit náhradní hodnoty za běhu, nezadávejte DECLARE_REGISTRY_RESOURCE nebo DECLARE_REGISTRY_RESOURCEID makro. Místo toho vytvořte `_ATL_REGMAP_ENTRIES` pole struktur, kde každá položka obsahuje variabilní zástupný symbol spárovaný s hodnotou, která nahradí zástupný symbol za běhu. Potom `UpdateRegistryFromResourceD`volání , předání pole pro *pMapEntries* parametr. Tím se všechny náhradní `_ATL_REGMAP_ENTRIES` hodnoty ve strukturách přidá do náhradní mapy registrátora.

> [!NOTE]
> Chcete-li staticky propojit součást registru ATL (registrátor), přečtěte si článek [UpdateRegistryFromResourceS](#updateregistryfromresources).

Další informace o nahraditelných parametrech a skriptování naleznete v článku [Součást registru ATL (registrátor)](../../atl/atl-registry-component-registrar.md).

## <a name="ccommoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a>Ccommodule::UpdateRegistryFromResources

Od ATL 7.0, `CComModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

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

*lpszRes*<br/>
[v] Název prostředku.

*nResID*<br/>
[v] ID prostředku.

*bRegistrovat*<br/>
[v] Označuje, zda má být skript prostředku zaregistrován.

*pMapEntries*<br/>
[v] Ukazatel na náhradní mapu ukládající hodnoty přidružené k nahraditelným parametrům skriptu. Atl automaticky `%MODULE%`používá . Chcete-li použít další nahraditelné parametry, naleznete podrobnosti v části Poznámky. V opačném případě použijte výchozí hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Podobně jako [UpdateRegistryFromResourceD](#updateregistryfromresourced) s výjimkou `UpdateRegistryFromResourceS` vytvoří statické propojení s součástí registru ATL (registrátor).

`UpdateRegistryFromResourceS`bude vyvolána automaticky při zpracování mapy objektů za `#define _ATL_STATIC_REGISTRY` předpokladu, že přidáte do *pch.h* *(stdafx.h* v sadě Visual Studio 2017 a starší).

> [!NOTE]
> Chcete-li nahradit náhradní hodnoty za běhu, nezadávejte [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) ani [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) makro. Místo toho vytvořte `_ATL_REGMAP_ENTRIES` pole struktur, kde každá položka obsahuje variabilní zástupný symbol spárovaný s hodnotou, která nahradí zástupný symbol za běhu. Potom `UpdateRegistryFromResourceS`volání , předání pole pro *pMapEntries* parametr. Tím se všechny náhradní `_ATL_REGMAP_ENTRIES` hodnoty ve strukturách přidá do náhradní mapy registrátora.

Další informace o nahraditelných parametrech a skriptování naleznete v článku [Součást registru ATL (registrátor)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
