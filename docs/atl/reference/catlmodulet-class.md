---
title: CAtlModuleT – třída
ms.date: 11/04/2016
f1_keywords:
- CAtlModuleT
- ATLBASE/ATL::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::InitLibId
- ATLBASE/ATL::CAtlModuleT::RegisterAppId
- ATLBASE/ATL::CAtlModuleT::RegisterServer
- ATLBASE/ATL::CAtlModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlModuleT::UnregisterServer
- ATLBASE/ATL::CAtlModuleT::UpdateRegistryAppId
helpviewer_keywords:
- CAtlModuleT class
ms.assetid: 9b74d02f-9117-47b1-a05e-c5945f83dd2b
ms.openlocfilehash: b07e60265570e66337a2d13007e9ad57c6f369e4
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167861"
---
# <a name="catlmodulet-class"></a>CAtlModuleT – třída

Tato třída implementuje modul ATL.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída je odvozena z `CAtlModuleT`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlModuleT::InitLibId](#initlibid)|Inicializuje datový člen obsahující identifikátor GUID aktuálního modulu.|
|[CAtlModuleT::RegisterAppId](#registerappid)|Přidá EXE do registru.|
|[CAtlModuleT::RegisterServer](#registerserver)|Přidá službu do registru.|
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|Odebere EXE z registru.|
|[CAtlModuleT::UnregisterServer](#unregisterserver)|Odebere službu z registru.|
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|Aktualizuje informace EXE v registru.|

## <a name="remarks"></a>Poznámky

`CAtlModuleT`odvozený z [CAtlModule](../../atl/reference/catlmodule-class.md)implementuje SPUSTITELNÝ (exe) nebo modul ATL služby (exe). Spustitelný modul je místní, mimoprocesové Server, zatímco modul služby je aplikace systému Windows, která běží na pozadí při spuštění systému Windows.

`CAtlModuleT`poskytuje podporu pro inicializaci, registraci a zrušení registrace modulu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="catlmoduletcatlmodulet"></a><a name="catlmodulet"></a>CAtlModuleT::CAtlModuleT

Konstruktor

```cpp
CAtlModuleT() throw();
```

### <a name="remarks"></a>Poznámky

Volá [CAtlModuleT:: InitLibId](#initlibid).

## <a name="catlmoduletinitlibid"></a><a name="initlibid"></a>CAtlModuleT::InitLibId

Inicializuje datový člen obsahující identifikátor GUID aktuálního modulu.

```cpp
static void InitLibId() throw();
```

### <a name="remarks"></a>Poznámky

Volá se konstruktorem [CAtlModuleT:: CAtlModuleT](#catlmodulet).

## <a name="catlmoduletregisterappid"></a><a name="registerappid"></a>CAtlModuleT::RegisterAppId

Přidá EXE do registru.

```cpp
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

## <a name="catlmoduletregisterserver"></a><a name="registerserver"></a>CAtlModuleT::RegisterServer

Přidá službu do registru.

```cpp
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
TRUE, pokud má být zaregistrována knihovna typů. Výchozí hodnota je FALSE (NEPRAVDA).

*pCLSID*<br/>
Odkazuje na CLSID objektu, který má být zaregistrován. Pokud má hodnotu NULL (výchozí hodnota), budou zaregistrovány všechny objekty v mapě objektů.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

## <a name="catlmoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlModuleT::UnregisterAppId

Odebere EXE z registru.

```cpp
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

## <a name="catlmoduletunregisterserver"></a><a name="unregisterserver"></a>CAtlModuleT::UnregisterServer

Odebere službu z registru.

```cpp
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parametry

*bUnRegTypeLib*<br/>
TRUE, pokud je také zrušena registrace knihovny typů.

*pCLSID*<br/>
Odkazuje na CLSID objektu, který se má odregistrovat. Pokud má hodnotu NULL (výchozí hodnota), všechny objekty v mapě objektů budou odregistrovány.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

## <a name="catlmoduletupdateregistryappid"></a><a name="updateregistryappid"></a>CAtlModuleT::UpdateRegistryAppId

Aktualizuje informace EXE v registru.

```cpp
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>Parametry

*bRegister*<br/>
Vyhrazeno.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

## <a name="see-also"></a>Viz také

[CAtlModule – třída](../../atl/reference/catlmodule-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
