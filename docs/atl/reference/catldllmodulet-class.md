---
title: CAtlDllModuleT – třída
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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418067"
---
# <a name="catldllmodulet-class"></a>CAtlDllModuleT – třída

Tato třída reprezentuje modul pro knihovnu DLL.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše třída je odvozena z `CAtlDllModuleT`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlDllModuleT::CAtlDllModuleT](#catldllmodulet)|Konstruktor|
|[CAtlDllModuleT:: ~ CAtlDllModuleT](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlDllModuleT::D llCanUnloadNow](#dllcanunloadnow)|Testuje, zda může být knihovna DLL uvolněna.|
|[CAtlDllModuleT::D llGetClassObject](#dllgetclassobject)|Vrátí objekt pro vytváření tříd.|
|[CAtlDllModuleT::D llMain](#dllmain)|Volitelný vstupní bod do knihovny DLL (Dynamic-Link Library).|
|[CAtlDllModuleT::D llRegisterServer](#dllregisterserver)|Přidá položky do systémového registru pro objekty v knihovně DLL.|
|[CAtlDllModuleT::D llUnregisterServer](#dllunregisterserver)|Odebere položky v systémovém registru pro objekty v knihovně DLL.|
|[CAtlDllModuleT:: GetClassObject –](#getclassobject)|Vrátí objekt pro vytváření tříd. Vyvoláno pomocí [DllGetClassObject](#dllgetclassobject).|

## <a name="remarks"></a>Poznámky

`CAtlDllModuleT` představuje modul pro dynamickou knihovnu (DLL) a poskytuje funkce používané všemi projekty knihovny DLL. Tato specializace třídy [CAtlModuleT](../../atl/reference/catlmodulet-class.md) zahrnuje podporu pro registraci.

Další informace o modulech v knihovně ATL naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="catldllmodulet"></a>CAtlDllModuleT::CAtlDllModuleT

Konstruktor

```
CAtlDllModuleT() throw();
```

##  <a name="dtor"></a>CAtlDllModuleT:: ~ CAtlDllModuleT

Destruktor.

```
~CAtlDllModuleT() throw();
```

##  <a name="dllcanunloadnow"></a>CAtlDllModuleT::D llCanUnloadNow

Testuje, zda může být knihovna DLL uvolněna.

```
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK, pokud může být knihovna DLL uvolněna nebo S_FALSE, pokud nemůže.

##  <a name="dllgetclassobject"></a>CAtlDllModuleT::D llGetClassObject

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
IID požadovaného rozhraní.

*ppv*<br/>
Ukazatel na ukazatel rozhraní identifikovaný *riid*. Pokud objekt nepodporuje toto rozhraní, je *PPV* nastaveno na hodnotu null.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="dllmain"></a>CAtlDllModuleT::D llMain

Volitelný vstupní bod do knihovny DLL (Dynamic-Link Library).

```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>Parametry

*Parametr dwReason*<br/>
Pokud je nastaveno na DLL_PROCESS_ATTACH, jsou volání oznámení DLL_THREAD_ATTACH a DLL_THREAD_DETACH zakázána.

*lpReserved*<br/>
Rezervovaný.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Zakázání volání oznámení DLL_THREAD_ATTACH a DLL_THREAD_DETACH může být užitečnou optimalizací pro vícevláknové aplikace, které mají mnoho knihoven DLL, které často vytvářejí a odstraňují vlákna a jejichž knihovny DLL nepotřebují tato oznámení na úrovni vlákna pro přílohy a odpojení.

##  <a name="dllregisterserver"></a>CAtlDllModuleT::D llRegisterServer

Přidá položky do systémového registru pro objekty v knihovně DLL.

```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
TRUE, pokud má být zaregistrována knihovna typů. Výchozí hodnota je TRUE (pravda).

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="dllunregisterserver"></a>CAtlDllModuleT::D llUnregisterServer

Odebere položky v systémovém registru pro objekty v knihovně DLL.

```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parametry

*bUnRegTypeLib*<br/>
TRUE, pokud má být knihovna typů odebrána z registru. Výchozí hodnota je TRUE (pravda).

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="getclassobject"></a>CAtlDllModuleT:: GetClassObject –

Vytvoří objekt zadaného objektu CLSID.

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
IID požadovaného rozhraní.

*ppv*<br/>
Ukazatel na ukazatel rozhraní identifikovaný *riid*. Pokud objekt nepodporuje toto rozhraní, je *PPV* nastaveno na hodnotu null.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tuto metodu volá [CAtlDllModuleT::D llgetclassobject](#dllgetclassobject) a je zahrnutá z důvodu zpětné kompatibility.

## <a name="see-also"></a>Viz také

[CAtlModuleT – třída](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlExeModuleT – třída](../../atl/reference/catlexemodulet-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
