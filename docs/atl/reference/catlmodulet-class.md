---
title: Catlmodulet – třída
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
ms.openlocfilehash: 2cd207038a92b944bf95575f0e0c820b8f09d615
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272045"
---
# <a name="catlmodulet-class"></a>Catlmodulet – třída

Tato třída implementuje modul knihovny ATL.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `CAtlModuleT`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlModuleT::InitLibId](#initlibid)|Inicializuje datový člen obsahující identifikátor GUID aktuálního modulu.|
|[CAtlModuleT::RegisterAppId](#registerappid)|Přidá soubor EXE do registru.|
|[CAtlModuleT::RegisterServer](#registerserver)|Přidá služby do registru.|
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|Odebere soubor EXE z registru.|
|[CAtlModuleT::UnregisterServer](#unregisterserver)|Odebere službu z registru.|
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|Aktualizuje informace o souboru EXE v registru.|

## <a name="remarks"></a>Poznámky

`CAtlModuleT`, odvozený z [catlmodule –](../../atl/reference/catlmodule-class.md), implementuje modul služby (EXE) knihovny ATL nebo spustitelný soubor (EXE). Spustitelný soubor modulu je serveru místní, mimo proces, že modul Service je aplikace Windows, na kterém běží na pozadí při spuštění Windows.

`CAtlModuleT` poskytuje podporu pro inicializaci, registrace a zrušení registrace modulu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="catlmodulet"></a>  CAtlModuleT::CAtlModuleT

Konstruktor

```
CAtlModuleT() throw();
```

### <a name="remarks"></a>Poznámky

Volání [CAtlModuleT::InitLibId](#initlibid).

##  <a name="initlibid"></a>  CAtlModuleT::InitLibId

Inicializuje datový člen obsahující identifikátor GUID aktuálního modulu.

```
static void InitLibId() throw();
```

### <a name="remarks"></a>Poznámky

Volá konstruktor [CAtlModuleT::CAtlModuleT](#catlmodulet).

##  <a name="registerappid"></a>  CAtlModuleT::RegisterAppId

Přidá soubor EXE do registru.

```
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="registerserver"></a>  CAtlModuleT::RegisterServer

Přidá služby do registru.

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
TRUE, pokud knihovna typů je k registraci. Výchozí hodnota je FALSE.

*pCLSID*<br/>
Odkazuje na identifikátor CLSID objekt, který má být zaregistrován. Pokud se zaregistruje NULL (výchozí hodnota), všechny objekty v mapě objektů.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="unregisterappid"></a>  CAtlModuleT::UnregisterAppId

Odebere soubor EXE z registru.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="unregisterserver"></a>  CAtlModuleT::UnregisterServer

Odebere službu z registru.

```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parametry

*bUnRegTypeLib*<br/>
TRUE, pokud knihovna typů je také možné odregistrovat.

*pCLSID*<br/>
Odkazuje na identifikátor CLSID objekt, který má být zrušena registrace. Pokud hodnotu NULL (výchozí hodnota), všechny objekty v mapě objektů bude zrušena.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="updateregistryappid"></a>  CAtlModuleT::UpdateRegistryAppId

Aktualizuje informace o souboru EXE v registru.

```
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>Parametry

*bRegister*<br/>
Vyhrazená.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

## <a name="see-also"></a>Viz také:

[CAtlModule – třída](../../atl/reference/catlmodule-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
