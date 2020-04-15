---
title: Třída CAtlModuleT
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
ms.openlocfilehash: bf64c073249b7426fafb430a708573d9d06d11fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321415"
---
# <a name="catlmodulet-class"></a>Třída CAtlModuleT

Tato třída implementuje modul ATL.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozená z `CAtlModuleT`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlModuleT::InitLibId](#initlibid)|Inicializuje datový člen obsahující identifikátor GUID aktuálního modulu.|
|[CAtlModuleT::RegisterAppId](#registerappid)|Přidá EXE do registru.|
|[CAtlModuleT::RegisterServer](#registerserver)|Přidá službu do registru.|
|[CAtlModuleT::Zrušení registrace Id](#unregisterappid)|Odebere EXE z registru.|
|[CAtlModuleT::UnregisterServer](#unregisterserver)|Odebere službu z registru.|
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|Aktualizuje informace EXE v registru.|

## <a name="remarks"></a>Poznámky

`CAtlModuleT`, odvozený z [CAtlModule](../../atl/reference/catlmodule-class.md), implementuje spustitelný (EXE) nebo servisní (EXE) modul ATL. Spustitelný modul je místní mimoprocesový server, zatímco modul Service je aplikace systému Windows, která běží na pozadí při spuštění systému Windows.

`CAtlModuleT`poskytuje podporu pro inicializaci, registraci a zrušení registrace modulu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[Modul CAtl](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="catlmoduletcatlmodulet"></a><a name="catlmodulet"></a>CAtlModuleT::CAtlModuleT

Konstruktor

```
CAtlModuleT() throw();
```

### <a name="remarks"></a>Poznámky

Volá [CAtlModuleT::InitLibId](#initlibid).

## <a name="catlmoduletinitlibid"></a><a name="initlibid"></a>CAtlModuleT::InitLibId

Inicializuje datový člen obsahující identifikátor GUID aktuálního modulu.

```
static void InitLibId() throw();
```

### <a name="remarks"></a>Poznámky

Volat [konstruktoru CAtlModuleT::CAtlModuleT](#catlmodulet).

## <a name="catlmoduletregisterappid"></a><a name="registerappid"></a>CAtlModuleT::RegisterAppId

Přidá EXE do registru.

```
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="catlmoduletregisterserver"></a><a name="registerserver"></a>CAtlModuleT::RegisterServer

Přidá službu do registru.

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
TRUE, pokud má být knihovna typů registrována. Výchozí hodnota je FALSE.

*pCLSID*<br/>
Odkazuje na CLSID objektu, který má být registrován. Pokud null (výchozí hodnota), budou zaregistrovány všechny objekty v mapě objektů.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="catlmoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlModuleT::Zrušení registrace Id

Odebere EXE z registru.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="catlmoduletunregisterserver"></a><a name="unregisterserver"></a>CAtlModuleT::UnregisterServer

Odebere službu z registru.

```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parametry

*bUnRegTypeLib*<br/>
TRUE, pokud má být knihovna typů také neregistrována.

*pCLSID*<br/>
Odkazuje na CLSID objektu, který má být neregistrován. Pokud null (výchozí hodnota), všechny objekty v mapě objektu budou unregistered.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="catlmoduletupdateregistryappid"></a><a name="updateregistryappid"></a>CAtlModuleT::UpdateRegistryAppId

Aktualizuje informace EXE v registru.

```
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>Parametry

*bRegistrovat*<br/>
Vyhrazeno.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="see-also"></a>Viz také

[Třída CAtlModule](../../atl/reference/catlmodule-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
