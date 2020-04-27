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
ms.openlocfilehash: e0896a28c24877465213a71ac5207c537c731003
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168761"
---
# <a name="catldllmodulet-class"></a>CAtlDllModuleT – třída

Tato třída reprezentuje modul pro knihovnu DLL.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

### <a name="parameters"></a>Parametry

*T*<br/>
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

`CAtlDllModuleT`představuje modul pro dynamickou knihovnu (DLL) a poskytuje funkce používané všemi projekty knihovny DLL. Tato specializace třídy [CAtlModuleT](../../atl/reference/catlmodulet-class.md) zahrnuje podporu pro registraci.

Další informace o modulech v knihovně ATL naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="catldllmoduletcatldllmodulet"></a><a name="catldllmodulet"></a>CAtlDllModuleT::CAtlDllModuleT

Konstruktor

```cpp
CAtlDllModuleT() throw();
```

## <a name="catldllmoduletcatldllmodulet"></a><a name="dtor"></a>CAtlDllModuleT:: ~ CAtlDllModuleT

Destruktor.

```cpp
~CAtlDllModuleT() throw();
```

## <a name="catldllmoduletdllcanunloadnow"></a><a name="dllcanunloadnow"></a>CAtlDllModuleT::D llCanUnloadNow

Testuje, zda může být knihovna DLL uvolněna.

```cpp
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK, pokud může být knihovna DLL uvolněna nebo S_FALSE, pokud nemůže.

## <a name="catldllmoduletdllgetclassobject"></a><a name="dllgetclassobject"></a>CAtlDllModuleT::D llGetClassObject

Vrátí objekt pro vytváření tříd.

```cpp
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

## <a name="catldllmoduletdllmain"></a><a name="dllmain"></a>CAtlDllModuleT::D llMain

Volitelný vstupní bod do knihovny DLL (Dynamic-Link Library).

```cpp
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>Parametry

*Parametr dwReason*<br/>
Pokud je nastaveno na DLL_PROCESS_ATTACH, jsou volání oznámení DLL_THREAD_ATTACH a DLL_THREAD_DETACH zakázána.

*lpReserved*<br/>
Vyhrazeno.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Zakázání volání oznámení DLL_THREAD_ATTACH a DLL_THREAD_DETACH může být užitečnou optimalizací pro vícevláknové aplikace, které mají mnoho knihoven DLL, které často vytvářejí a odstraňují vlákna a jejichž knihovny DLL nepotřebují tato oznámení na úrovni vlákna pro přílohy a odpojení.

## <a name="catldllmoduletdllregisterserver"></a><a name="dllregisterserver"></a>CAtlDllModuleT::D llRegisterServer

Přidá položky do systémového registru pro objekty v knihovně DLL.

```cpp
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
TRUE, pokud má být zaregistrována knihovna typů. Výchozí hodnota je TRUE (pravda).

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

## <a name="catldllmoduletdllunregisterserver"></a><a name="dllunregisterserver"></a>CAtlDllModuleT::D llUnregisterServer

Odebere položky v systémovém registru pro objekty v knihovně DLL.

```cpp
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parametry

*bUnRegTypeLib*<br/>
TRUE, pokud má být knihovna typů odebrána z registru. Výchozí hodnota je TRUE (pravda).

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

## <a name="catldllmoduletgetclassobject"></a><a name="getclassobject"></a>CAtlDllModuleT:: GetClassObject –

Vytvoří objekt zadaného objektu CLSID.

```cpp
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
