---
title: CAtlDllModuleT Class
ms.date: 11/04/2016
f1_keywords:
- CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::DllCanUnloadNow
- ATLBASE/ATL::CAtlDllModuleT::DllGetClassObject
- ATLBASE/ATL::CAtlDllModuleT::DllMain
- ATLBASE/ATL::CAtlDllModuleT::DllRegisterServer
- ATLBASE/ATL::CAtlDllModuleT::DllUnregisterServer
- ATLBASE/ATL::CAtlDllModuleT::GetClassObject
helpviewer_keywords:
- CAtlDllModuleT class
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
ms.openlocfilehash: be42915c6c2e941bc5fc1de78c5c7ac26ccca6e2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259214"
---
# <a name="catldllmodulet-class"></a>CAtlDllModuleT Class

Tato třída reprezentuje modulu pro knihovnu DLL.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `CAtlDllModuleT`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlDllModuleT::CAtlDllModuleT](#catldllmodulet)|Konstruktor|
|[CAtlDllModuleT::~CAtlDllModuleT](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlDllModuleT::DllCanUnloadNow](#dllcanunloadnow)|Testuje, zda je knihovna DLL může být uvolněna.|
|[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)|Vrátí objekt pro vytváření tříd.|
|[CAtlDllModuleT::DllMain](#dllmain)|Volitelné vstupní bod do dynamická knihovna (DLL).|
|[CAtlDllModuleT::DllRegisterServer](#dllregisterserver)|Přidá položky do systémového registru pro objekty v knihovně DLL.|
|[CAtlDllModuleT::DllUnregisterServer](#dllunregisterserver)|Odebere položky systémového registru pro objekty v knihovně DLL.|
|[CAtlDllModuleT::GetClassObject](#getclassobject)|Vrátí objekt pro vytváření tříd. Vyvolaná podle [DllGetClassObject](#dllgetclassobject).|

## <a name="remarks"></a>Poznámky

`CAtlDllModuleT` představuje modul pro dynamická knihovna (DLL) a poskytuje funkce, které používají všechny projekty knihovny DLL. Tato specializace [catlmodulet –](../../atl/reference/catlmodulet-class.md) třída zahrnuje podporu pro registraci.

Další informace o modulech v ATL naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="catldllmodulet"></a>  CAtlDllModuleT::CAtlDllModuleT

Konstruktor

```
CAtlDllModuleT() throw();
```

##  <a name="dtor"></a>  CAtlDllModuleT::~CAtlDllModuleT

Destruktor.

```
~CAtlDllModuleT() throw();
```

##  <a name="dllcanunloadnow"></a>  CAtlDllModuleT::DllCanUnloadNow

Testuje, zda je knihovna DLL může být uvolněna.

```
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK, pokud se dá zrušit zavedení DLL nebo S_FALSE v případě nedostupnosti.

##  <a name="dllgetclassobject"></a>  CAtlDllModuleT::DllGetClassObject

Vrátí objekt pro vytváření tříd.

```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parametry

*rclsid*<br/>
Identifikátor CLSID objektu, který má být vytvořen.

*riid*<br/>
Identifikátor IID požadované rozhraní.

*ppv*<br/>
Ukazatel na ukazatel rozhraní, který je identifikován *riid*. Pokud objekt nepodporuje toto rozhraní *ppv* nastaven na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="dllmain"></a>  CAtlDllModuleT::DllMain

Volitelné vstupní bod do dynamická knihovna (DLL).

```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>Parametry

*dwReason*<br/>
Pokud je nastavený na DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH a DLL_THREAD_DETACH případně oznámení volání jsou zakázána.

*lpReserved*<br/>
Vyhrazená.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Zakazuje DLL_THREAD_ATTACH a DLL_THREAD_DETACH případně oznámení, že volání může být užitečné optimalizace pro vícevláknové aplikace, které mají mnoho knihoven DLL, který často vytvářet a odstraňovat vlákna, a jehož knihovny DLL nemusí tato oznámení na úrovni vlákna z přílohy/odpojení.

##  <a name="dllregisterserver"></a>  CAtlDllModuleT::DllRegisterServer

Přidá položky do systémového registru pro objekty v knihovně DLL.

```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
TRUE, pokud knihovna typů je k registraci. Výchozí hodnota je TRUE.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="dllunregisterserver"></a>  CAtlDllModuleT::DllUnregisterServer

Odebere položky systémového registru pro objekty v knihovně DLL.

```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parametry

*bUnRegTypeLib*<br/>
TRUE, pokud knihovna typů má být odebrán z registru. Výchozí hodnota je TRUE.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="getclassobject"></a>  CAtlDllModuleT::GetClassObject

Vytvoří objekt zadaným identifikátorem CLSID.

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parametry

*rclsid*<br/>
Identifikátor CLSID objektu, který má být vytvořen.

*riid*<br/>
Identifikátor IID požadované rozhraní.

*ppv*<br/>
Ukazatel na ukazatel rozhraní, který je identifikován *riid*. Pokud objekt nepodporuje toto rozhraní *ppv* nastaven na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda je volána metodou [CAtlDllModuleT::DllGetClassObject](#dllgetclassobject) a je součástí zpětné kompatibility.

## <a name="see-also"></a>Viz také:

[CAtlModuleT – třída](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlExeModuleT – třída](../../atl/reference/catlexemodulet-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
