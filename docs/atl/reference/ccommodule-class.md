---
title: CComModule – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 53138081a6d712f775a2cc8f1e6905c45d95d34d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497107"
---
# <a name="ccommodule-class"></a>CComModule – třída

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComModule:: GetClassObject –](#getclassobject)|Vytvoří objekt zadaného objektu CLSID. Pouze pro knihovny DLL.|
|[CComModule:: GetModuleInstance](#getmoduleinstance)|Vrátí `m_hInst`.|
|[CComModule:: GetResourceInstance](#getresourceinstance)|Vrátí `m_hInstResource`.|
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|Vrátí `m_hInstTypeLib`.|
|[CComModule:: init](#init)|Inicializuje datové členy.|
|[CComModule:: RegisterClassHelper](#registerclasshelper)|Zadá do systémového registru registraci standardní třídy objektu.|
|[CComModule:: RegisterClassObjects](#registerclassobjects)|Zaregistruje objekt třídy. Jenom pro exe.|
|[CComModule::RegisterServer](#registerserver)|Aktualizuje systémový registr pro každý objekt v mapě objektů.|
|[CComModule::RegisterTypeLib](#registertypelib)|Zaregistruje knihovnu typů.|
|[CComModule:: RevokeClassObjects](#revokeclassobjects)|Odvolá objekt třídy. Jenom pro exe.|
|[CComModule:: Term](#term)|Uvolňuje datové členy.|
|[CComModule:: UnregisterClassHelper](#unregisterclasshelper)|Odebere registraci standardní třídy objektu ze systémového registru.|
|[CComModule::UnregisterServer](#unregisterserver)|Zruší registraci každého objektu v mapě objektů.|
|[CComModule::UpdateRegistryClass](#updateregistryclass)|Registruje nebo zruší registraci standardní třídy objektu.|
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Spustí skript obsažený v zadaném prostředku k registraci nebo zrušení registrace objektu.|
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Staticky propojí komponentu registru ATL. Spustí skript obsažený v zadaném prostředku k registraci nebo zrušení registrace objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CComModule::m_csObjMap](#m_csobjmap)|Zajišťuje synchronizovaný přístup k informacím o mapě objektů.|
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|Zajišťuje synchronizovaný přístup k informacím o knihovně typů.|
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|Zajišťuje synchronizovaný přístup k informacím o třídě okna a ke statickým datům použitým během vytváření okna.|
|[CComModule::m_hInst](#m_hinst)|Obsahuje popisovač instance modulu.|
|[CComModule::m_hInstResource](#m_hinstresource)|Ve výchozím nastavení obsahuje popisovač instance modulu.|
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|Ve výchozím nastavení obsahuje popisovač instance modulu.|
|[CComModule::m_pObjMap](#m_pobjmap)|Odkazuje na mapu objektů udržované instancí modulu.|

## <a name="remarks"></a>Poznámky

> [!NOTE]
>  Tato třída je zastaralá a Průvodce generováním kódu ATL teď používá odvozené třídy [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) a [CAtlModule](../../atl/reference/catlmodule-class.md) . Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) . Níže uvedené informace jsou pro použití s aplikacemi vytvořenými staršími verzemi knihovny ATL. `CComModule`je stále součástí knihovny ATL pro funkci zpětného vyhledávání.

`CComModule`implementuje modul COM serveru a umožňuje klientovi přístup k součástem modulu. `CComModule`podporuje jak knihovny DLL (in-proces), tak i EXE (místní) moduly.

`CComModule` Instance používá mapu objektů k údržbě sady definic objektů třídy. Toto mapování objektů je implementováno jako pole `_ATL_OBJMAP_ENTRY` struktur a obsahuje informace pro:

- Zadávání a odebírání popisů objektů v systémovém registru.

- Vytváření instancí objektů prostřednictvím objektu pro vytváření tříd.

- Navazování komunikace mezi klientem a kořenovým objektem součásti.

- Provádění správy životnosti objektů třídy.

Když spustíte AppWizard ATL com, průvodce automaticky vygeneruje `_Module`, globální `CComModule` instanci nebo třídu odvozenou z ní. Další informace o Průvodci projektem ATL naleznete v článku [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md).

Kromě `CComModule`toho ATL poskytuje [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), který implementuje modul modelu apartment pro exe a služby systému Windows. Odvodit modul z `CComAutoThreadModule` , pokud chcete vytvořit objekty ve více objektech Apartment.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="getclassobject"></a>CComModule:: GetClassObject –

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parametry

*rclsid*<br/>
pro Identifikátor CLSID objektu, který má být vytvořen.

*riid*<br/>
pro IID požadovaného rozhraní.

*ppv*<br/>
mimo Ukazatel na ukazatel rozhraní identifikovaný *riid*. Pokud objekt nepodporuje toto rozhraní, je *PPV* nastaveno na hodnotu null.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Vytvoří objekt zadaného identifikátoru CLSID a načte ukazatel rozhraní na tento objekt.

`GetClassObject`je k dispozici pouze pro knihovny DLL.

##  <a name="getmoduleinstance"></a>CComModule:: GetModuleInstance

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Návratová hodnota

HINSTANCE identifikující tento modul.

### <a name="remarks"></a>Poznámky

Vrátí datový člen [m_hInst](#m_hinst) .

##  <a name="getresourceinstance"></a>CComModule:: GetResourceInstance

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Návratová hodnota

HINSTANCE.

### <a name="remarks"></a>Poznámky

Vrátí datový člen [m_hInstResource](#m_hinstresource) .

##  <a name="gettypelibinstance"></a>CComModule:: GetTypeLibInstance

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>Návratová hodnota

HINSTANCE.

### <a name="remarks"></a>Poznámky

Vrátí datový člen [m_hInstTypeLib](#m_hinsttypelib) .

##  <a name="init"></a>CComModule:: init

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
pro Ukazatel na pole položek mapy objektů.

*h*<br/>
pro HINSTANCE předaný do `DLLMain` nebo `WinMain`.

*plibid*<br/>
pro Ukazatel na LIBID knihovny typů přidružené k projektu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Inicializuje všechny datové členy.

##  <a name="m_csobjmap"></a>  CComModule::m_csObjMap

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>Poznámky

Zajišťuje synchronizovaný přístup k mapě objektů.

##  <a name="m_cstypeinfoholder"></a>  CComModule::m_csTypeInfoHolder

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>Poznámky

Zajišťuje synchronizovaný přístup k knihovně typů.

##  <a name="m_cswindowcreate"></a>  CComModule::m_csWindowCreate

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>Poznámky

Zajišťuje synchronizovaný přístup k informacím o třídě okna a ke statickým datům použitým během vytváření okna.

##  <a name="m_hinst"></a>CComModule:: m_hInst

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>Poznámky

Obsahuje popisovač instance modulu.

Metoda [init](#init) se nastaví `m_hInst` na popisovač předaný do `DLLMain` nebo `WinMain`.

##  <a name="m_hinstresource"></a>CComModule:: m_hInstResource

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení obsahuje popisovač instance modulu.

Metoda [init](#init) se nastaví `m_hInstResource` na popisovač předaný do `DLLMain` nebo `WinMain`. Můžete explicitně nastavit `m_hInstResource` popisovač na prostředek.

Metoda [GetResourceInstance](#getresourceinstance) vrací popisovač uložený v `m_hInstResource`.

##  <a name="m_hinsttypelib"></a>  CComModule::m_hInstTypeLib

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení obsahuje popisovač instance modulu.

Metoda [init](#init) se nastaví `m_hInstTypeLib` na popisovač předaný do `DLLMain` nebo `WinMain`. Můžete explicitně nastavit `m_hInstTypeLib` popisovač na knihovnu typů.

Metoda [GetTypeLibInstance](#gettypelibinstance) vrací popisovač uložený v `m_hInstTypeLib`.

##  <a name="m_pobjmap"></a>  CComModule::m_pObjMap

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>Poznámky

Odkazuje na mapu objektů udržované instancí modulu.

##  <a name="registerclasshelper"></a>CComModule:: RegisterClassHelper

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
ATL_DEPRECATED HRESULT RegisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*CLSID*<br/>
pro Identifikátor CLSID objektu, který má být zaregistrován.

*lpszProgID*<br/>
pro Identifikátor ProgID přidružený k objektu.

*lpszVerIndProgID*<br/>
pro Identifikátor ProgID nezávislý na verzi přidružený k objektu.

*nDescID*<br/>
pro Identifikátor prostředku řetězce pro popis objektu.

*dwFlags*<br/>
pro Určuje model dělení na vlákna, který se má zadat do registru. Možné hodnoty jsou THREADFLAGS_APARTMENT, THREADFLAGS_BOTH nebo AUTPRXFLAG.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Zadá do systémového registru registraci standardní třídy objektu.

Metoda [UpdateRegistryClass](#updateregistryclass) volá `RegisterClassHelper`.

##  <a name="registerclassobjects"></a>CComModule:: RegisterClassObjects

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parametry

*dwClsContext*<br/>
pro Určuje kontext, ve kterém má být objekt třídy spuštěn. Možné hodnoty jsou CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER nebo CLSCTX_LOCAL_SERVER. Popis těchto hodnot naleznete v tématu [CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) v Windows SDK.

*dwFlags*<br/>
pro Určuje typy připojení k objektu třídy. Možné hodnoty jsou REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE nebo REGCLS_MULTI_SEPARATE. Popis těchto hodnot naleznete v tématu [REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Zaregistruje objekt třídy EXE s OLE, aby se k němu mohli připojit jiné aplikace. Tato metoda je k dispozici pouze pro exe.

##  <a name="registerserver"></a>CComModule:: RegisterServer

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
pro Určuje, zda bude knihovna typů zaregistrována. Výchozí hodnota je FALSE (NEPRAVDA).

*pCLSID*<br/>
pro Odkazuje na CLSID objektu, který má být zaregistrován. Pokud má hodnotu NULL (výchozí hodnota), budou zaregistrovány všechny objekty v mapě objektů.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

V závislosti na parametru *pCLSID* aktualizuje systémový registr pro jeden objekt třídy nebo pro všechny objekty v mapě objektů.

Pokud má *bRegTypeLib* hodnotu true, budou aktualizovány také informace o knihovně typů.

Informace o tom, jak přidat položku do mapy objektů, naleznete v tématu [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) .

`RegisterServer`bude volána automaticky `DLLRegisterServer` pro knihovnu DLL `WinMain` nebo pro spuštění s `/RegServer` možností příkazového řádku.

##  <a name="registertypelib"></a>CComModule:: RegisterTypeLib

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
pro Řetězec ve formátu `"\\N"`, kde `N` je celočíselný index prostředku TYPELIB.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Přidá do systémového registru informace o knihovně typů.

Pokud instance modulu obsahuje více knihoven typů, použijte druhou verzi této metody k určení, která knihovna typů má být použita.

##  <a name="revokeclassobjects"></a>CComModule:: RevokeClassObjects

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Odebere objekt třídy. Tato metoda je k dispozici pouze pro exe.

##  <a name="term"></a>CComModule:: Term

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
void Term() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny datové členy.

##  <a name="unregisterclasshelper"></a>CComModule:: UnregisterClassHelper

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>Parametry

*CLSID*<br/>
pro Identifikátor CLSID objektu, který má být zaregistrován.

*lpszProgID*<br/>
pro Identifikátor ProgID přidružený k objektu.

*lpszVerIndProgID*<br/>
pro Identifikátor ProgID nezávislý na verzi přidružený k objektu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Odebere registraci standardní třídy objektu ze systémového registru.

Metoda [UpdateRegistryClass](#updateregistryclass) volá `UnregisterClassHelper`.

##  <a name="unregisterserver"></a>CComModule:: UnregisterServer

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>Parametry

*bUnRegTypeLib*<br/>
Je-li nastavena hodnota TRUE, je také zrušena registrace knihovny typů.

*pCLSID*<br/>
Odkazuje na CLSID objektu, který se má odregistrovat. Pokud má hodnotu NULL (výchozí hodnota), všechny objekty v mapě objektů budou odregistrovány.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

V závislosti na parametru *pCLSID* zruší registraci jediného objektu třídy nebo všech objektů v mapě objektů.

`UnregisterServer`bude volána automaticky `DLLUnregisterServer` pro knihovnu DLL `WinMain` nebo pro spuštění s `/UnregServer` možností příkazového řádku.

Informace o tom, jak přidat položku do mapy objektů, naleznete v tématu [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) .

##  <a name="updateregistryclass"></a>CComModule:: UpdateRegistryClass

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

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

*CLSID*<br/>
Identifikátor CLSID objektu, který má být zaregistrován nebo odregistrován.

*lpszProgID*<br/>
Identifikátor ProgID přidružený k objektu.

*lpszVerIndProgID*<br/>
Identifikátor ProgID nezávislý na verzi přidružený k objektu.

*nDescID*<br/>
Identifikátor prostředku řetězce pro popis objektu.

*szDesc*<br/>
Řetězec obsahující popis objektu.

*dwFlags*<br/>
Určuje model dělení na vlákna, který se má zadat do registru. Možné hodnoty jsou THREADFLAGS_APARTMENT, THREADFLAGS_BOTH nebo AUTPRXFLAG.

*bRegister*<br/>
Určuje, zda má být objekt zaregistrován.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pokud má *bRegister* hodnotu true, tato metoda do systémového registru zadává registraci standardní třídy objektu.

Pokud je *BREGISTER* false, odebere registraci objektu.

V závislosti na hodnotě *bRegister* `UpdateRegistryClass` zavolá buď [RegisterClassHelper](#registerclasshelper) , nebo [UnregisterClassHelper](#unregisterclasshelper).

Zadáním `UpdateRegistryClass` makra [DECLARE_REGISTRY](registry-macros.md#declare_registry) se vyvolá automaticky při zpracování mapy objektů.

##  <a name="updateregistryfromresourced"></a>CComModule:: UpdateRegistryFromResourceD

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

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
pro Název prostředku.

*nResID*<br/>
pro ID prostředku.

*bRegister*<br/>
pro Určuje, zda má být objekt zaregistrován.

*pMapEntries*<br/>
pro Ukazatel na náhradní mapu ukládá hodnoty přidružené k nahraditelným parametrům skriptu. ATL automaticky používá `%MODULE%`. Informace o použití dalších nahraditelných parametrů naleznete v části poznámky. V opačném případě použijte výchozí hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Spustí skript obsažený v prostředku určeném parametrem *lpszRes* nebo *nResID*.

Pokud má *bRegister* hodnotu true, tato metoda registruje objekt v registru systému. v opačném případě zruší registraci objektu.

Zadáním `UpdateRegistryFromResourceD` makra [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) nebo [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) bude vyvoláno automaticky při zpracování mapy objektů.

> [!NOTE]
>  Chcete-li nahradit nahrazující hodnoty za běhu, nezadávejte makro DECLARE_REGISTRY_RESOURCE nebo DECLARE_REGISTRY_RESOURCEID. Místo toho vytvořte pole `_ATL_REGMAP_ENTRIES` struktur, kde každá položka obsahuje zástupný symbol s proměnnou s hodnotou, která nahradí zástupný symbol za běhu. Pak zavolejte `UpdateRegistryFromResourceD`a předejte pole pro parametr *pMapEntries* . Tím se ve `_ATL_REGMAP_ENTRIES` strukturách přidají všechny nahrazující hodnoty pro náhradní mapu registrátora.

> [!NOTE]
>  Chcete-li staticky propojit komponentu registru knihovny ATL (registrátor), přečtěte si téma [UpdateRegistryFromResourceS](#updateregistryfromresources).

Další informace o nahraditelných parametrech a skriptování naleznete v článku [Komponenta registru ATL (registrátor)](../../atl/atl-registry-component-registrar.md).

##  <a name="updateregistryfromresources"></a>CComModule:: UpdateRegistryFromResourceS

Od ATL 7,0 `CComModule` je zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

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
pro Název prostředku.

*nResID*<br/>
pro ID prostředku.

*bRegister*<br/>
pro Určuje, zda má být zaregistrován skript prostředků.

*pMapEntries*<br/>
pro Ukazatel na náhradní mapu ukládá hodnoty přidružené k nahraditelným parametrům skriptu. ATL automaticky používá `%MODULE%`. Informace o použití dalších nahraditelných parametrů naleznete v části poznámky. V opačném případě použijte výchozí hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Podobně jako [UpdateRegistryFromResourceD](#updateregistryfromresourced) s `UpdateRegistryFromResourceS` tím rozdílem, že vytvoří statický odkaz na komponentu registru ATL (registrátor).

`UpdateRegistryFromResourceS`bude vyvolána automaticky při zpracování mapy objektů za předpokladu, že přidáte `#define _ATL_STATIC_REGISTRY` do souboru stdafx. h.

> [!NOTE]
>  Chcete-li nahradit nahrazující hodnoty za běhu, nezadávejte makro [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) nebo [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) . Místo toho vytvořte pole `_ATL_REGMAP_ENTRIES` struktur, kde každá položka obsahuje zástupný symbol s proměnnou s hodnotou, která nahradí zástupný symbol za běhu. Pak zavolejte `UpdateRegistryFromResourceS`a předejte pole pro parametr *pMapEntries* . Tím se ve `_ATL_REGMAP_ENTRIES` strukturách přidají všechny nahrazující hodnoty pro náhradní mapu registrátora.

Další informace o nahraditelných parametrech a skriptování naleznete v článku [Komponenta registru ATL (registrátor)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
