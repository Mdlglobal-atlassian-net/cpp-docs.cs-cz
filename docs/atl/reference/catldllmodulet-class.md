---
title: Třída CAtlDllModuleT
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
ms.openlocfilehash: 7a5f8e7e489c8e0d573569ac7c4a8fb63f652732
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319005"
---
# <a name="catldllmodulet-class"></a>Třída CAtlDllModuleT

Tato třída představuje modul pro DLL.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozená z `CAtlDllModuleT`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlDllModuleT::CAtlDllModuleT](#catldllmodulet)|Konstruktor|
|[CAtlDllModuleT::~CAtlDllModuleT](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlDllModuleT::DllCanUnloadNow](#dllcanunloadnow)|Testy, pokud dll lze uvolnit.|
|[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)|Vrátí třídu factory.|
|[CAtlDllModuleT::DllMain](#dllmain)|Volitelný vstupní bod do dynamické knihovny (DLL).|
|[CAtlDllModuleT::DllRegisterServer](#dllregisterserver)|Přidá položky do systémového registru pro objekty v dll.|
|[CAtlDllModuleT::DllUnregisterServer](#dllunregisterserver)|Odebere položky v systémovém registru pro objekty v dll.|
|[CAtlDllModuleT::GetClassObject](#getclassobject)|Vrátí třídu factory. Vyvolána [DllGetClassObject](#dllgetclassobject).|

## <a name="remarks"></a>Poznámky

`CAtlDllModuleT`představuje modul pro dynamickou knihovnu (DLL) a poskytuje funkce používané všemi projekty Knihovny DLL. Tato specializace třídy [CAtlModuleT](../../atl/reference/catlmodulet-class.md) zahrnuje podporu pro registraci.

Další informace o modulech v atl naleznete v tématu [ATL Module Classes](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[Modul CAtl](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="catldllmoduletcatldllmodulet"></a><a name="catldllmodulet"></a>CAtlDllModuleT::CAtlDllModuleT

Konstruktor

```
CAtlDllModuleT() throw();
```

## <a name="catldllmoduletcatldllmodulet"></a><a name="dtor"></a>CAtlDllModuleT::~CAtlDllModuleT

Destruktor.

```
~CAtlDllModuleT() throw();
```

## <a name="catldllmoduletdllcanunloadnow"></a><a name="dllcanunloadnow"></a>CAtlDllModuleT::DllCanUnloadNow

Testy, pokud dll lze uvolnit.

```
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK, pokud lze dll uvolnit nebo S_FALSE, pokud nemůže.

## <a name="catldllmoduletdllgetclassobject"></a><a name="dllgetclassobject"></a>CAtlDllModuleT::DllGetClassObject

Vrátí třídu factory.

```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parametry

*rclsid (rclsid)*<br/>
CLSID objektu, který má být vytvořen.

*riid řekl:*<br/>
IID požadovanérozhraní.

*Ppv*<br/>
Ukazatel rozhraní určený *riid*. Pokud objekt nepodporuje toto rozhraní, *je hodnota ppv* nastavena na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="catldllmoduletdllmain"></a><a name="dllmain"></a>CAtlDllModuleT::DllMain

Volitelný vstupní bod do dynamické knihovny (DLL).

```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>Parametry

*dwReason*<br/>
Pokud je nastavena na DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH a DLL_THREAD_DETACH oznámení volání jsou zakázány.

*lpReserved*<br/>
Vyhrazeno.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu PRAVDA.

### <a name="remarks"></a>Poznámky

Zakázání DLL_THREAD_ATTACH a DLL_THREAD_DETACH oznámení volání může být užitečná optimalizace pro vícevláknové aplikace, které mají mnoho knihovny DLL, které často vytvářejí a odstraňují vlákna a jejichž knihovny DLL nepotřebují tato oznámení na úrovni vlákna přílohy nebo odpojení.

## <a name="catldllmoduletdllregisterserver"></a><a name="dllregisterserver"></a>CAtlDllModuleT::DllRegisterServer

Přidá položky do systémového registru pro objekty v dll.

```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
TRUE, pokud má být knihovna typů registrována. Výchozí hodnota je TRUE.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="catldllmoduletdllunregisterserver"></a><a name="dllunregisterserver"></a>CAtlDllModuleT::DllUnregisterServer

Odebere položky v systémovém registru pro objekty v dll.

```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parametry

*bUnRegTypeLib*<br/>
TRUE, pokud má být knihovna typů odebrána z registru. Výchozí hodnota je TRUE.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="catldllmoduletgetclassobject"></a><a name="getclassobject"></a>CAtlDllModuleT::GetClassObject

Vytvoří objekt zadaného identifikátoru CLSID.

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parametry

*rclsid (rclsid)*<br/>
CLSID objektu, který má být vytvořen.

*riid řekl:*<br/>
IID požadovanérozhraní.

*Ppv*<br/>
Ukazatel rozhraní určený *riid*. Pokud objekt nepodporuje toto rozhraní, *je hodnota ppv* nastavena na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda je volána [CAtlDllModuleT::DllGetClassObject](#dllgetclassobject) a je součástí zpětné kompatibility.

## <a name="see-also"></a>Viz také

[Třída CAtlModuleT](../../atl/reference/catlmodulet-class.md)<br/>
[Třída CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
