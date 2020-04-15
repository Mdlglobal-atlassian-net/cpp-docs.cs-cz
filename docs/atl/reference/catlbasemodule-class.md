---
title: Třída CAtlBaseModule
ms.date: 11/04/2016
f1_keywords:
- CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::AddResourceInstance
- ATLCORE/ATL::CAtlBaseModule::GetHInstanceAt
- ATLCORE/ATL::CAtlBaseModule::GetModuleInstance
- ATLCORE/ATL::CAtlBaseModule::GetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::RemoveResourceInstance
- ATLCORE/ATL::CAtlBaseModule::SetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::m_bInitFailed
helpviewer_keywords:
- CAtlBaseModule class
ms.assetid: 55ade80c-9b0c-4c51-933e-2158436c1096
ms.openlocfilehash: a55412eff18fd04ac4e41c0f001991c1cf725b9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321512"
---
# <a name="catlbasemodule-class"></a>Třída CAtlBaseModule

Tato třída je vytvořena instance v každém projektu ATL.

## <a name="syntax"></a>Syntaxe

```
class CAtlBaseModule : public _ATL_BASE_MODULE
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlBaseModule::CAtlBaseModule](#catlbasemodule)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|Přidá instanci prostředku do seznamu uložených popisovačů.|
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|Vrátí popisovač zadané instanci prostředku.|
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|Vrátí instanci `CAtlBaseModule` modulu z objektu.|
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|Vrátí instanci `CAtlBaseModule` prostředku z objektu.|
|[CAtlBaseModule::RemoveResourceInstance](#removeresourceinstance)|Odebere instanci prostředku ze seznamu uložených popisovačů.|
|[CAtlBaseModule::Instance SetResourceInstance](#setresourceinstance)|Nastaví instanci `CAtlBaseModule` prostředku objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlBaseModule::m_bInitFailed](#m_binitfailed)|Proměnná, která označuje, zda se nezdařila inicializace modulu.|

## <a name="remarks"></a>Poznámky

Instance `CAtlBaseModule` pojmenované _AtlBaseModule je k dispozici v každém projektu ATL, obsahující popisovač instance modulu, popisovač modulu obsahující prostředky (které ve výchozím nastavení jsou stejné) a pole popisovačů pro moduly poskytující primární prostředky. `CAtlBaseModule`bezpečně přístupné z více vláken.

Tato třída nahrazuje zastaralou třídu [CComModule](../../atl/reference/ccommodule-class.md) používanou v dřívějších verzích atl.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)

`CAtlBaseModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

## <a name="catlbasemoduleaddresourceinstance"></a><a name="addresourceinstance"></a>CAtlBaseModule::AddResourceInstance

Přidá instanci prostředku do seznamu uložených popisovačů.

```
bool AddResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parametry

*hInst*<br/>
Instance prostředku, kterou chcete přidat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud byl prostředek úspěšně přidán, false jinak.

## <a name="catlbasemodulecatlbasemodule"></a><a name="catlbasemodule"></a>CAtlBaseModule::CAtlBaseModule

Konstruktor

```
CAtlBaseModule() throw();
```

### <a name="remarks"></a>Poznámky

Vytvoří `CAtlBaseModule`.

## <a name="catlbasemodulegethinstanceat"></a><a name="gethinstanceat"></a>CAtlBaseModule::GetHInstanceAt

Vrátí popisovač zadané instanci prostředku.

```
HINSTANCE GetHInstanceAt(int i) throw();
```

### <a name="parameters"></a>Parametry

*I*<br/>
Číslo instance prostředku.

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač na instanci prostředku nebo null, pokud neexistuje žádná odpovídající instance prostředku.

## <a name="catlbasemodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CAtlBaseModule::GetModuleInstance

Vrátí instanci `CAtlBaseModule` modulu z objektu.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí instanci modulu.

## <a name="catlbasemodulegetresourceinstance"></a><a name="getresourceinstance"></a>CAtlBaseModule::GetResourceInstance

Vrátí instanci prostředku.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí instanci prostředku.

## <a name="catlbasemodulem_binitfailed"></a><a name="m_binitfailed"></a>CAtlBaseModule::m_bInitFailed

Proměnná, která označuje, zda se nezdařila inicializace modulu.

```
static bool m_bInitFailed;
```

### <a name="remarks"></a>Poznámky

True Pokud modul inicializován, false, pokud se nepodařilo inicializovat.

## <a name="catlbasemoduleremoveresourceinstance"></a><a name="removeresourceinstance"></a>CAtlBaseModule::RemoveResourceInstance

Odebere instanci prostředku ze seznamu uložených popisovačů.

```
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parametry

*hInst*<br/>
Instance prostředku odebrat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud byl prostředek úspěšně odebrán, jinak false.

## <a name="catlbasemodulesetresourceinstance"></a><a name="setresourceinstance"></a>CAtlBaseModule::Instance SetResourceInstance

Nastaví instanci `CAtlBaseModule` prostředku objektu.

```
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parametry

*hInst*<br/>
Nová instance prostředku.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovanou instanci prostředku.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
