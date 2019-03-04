---
title: CAtlBaseModule Class
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
ms.openlocfilehash: d382d1fe7d50a2fdeefc9b477625580792de7d6f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284759"
---
# <a name="catlbasemodule-class"></a>CAtlBaseModule Class

V každém projektu ATL je vytvořena instance této třídy.

## <a name="syntax"></a>Syntaxe

```
class CAtlBaseModule : public _ATL_BASE_MODULE
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlBaseModule::CAtlBaseModule](#catlbasemodule)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|Přidá instanci prostředku do seznamu uložených obslužné rutiny.|
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|Vrátí popisovač do instance zadaného prostředku.|
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|Vrátí instanci modulu z `CAtlBaseModule` objektu.|
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|Vrátí instanci prostředků z `CAtlBaseModule` objektu.|
|[CAtlBaseModule::RemoveResourceInstance](#removeresourceinstance)|Odebere instanci prostředků ze seznamu uložených obslužné rutiny.|
|[CAtlBaseModule::SetResourceInstance](#setresourceinstance)|Nastaví instance prostředku `CAtlBaseModule` objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CAtlBaseModule::m_bInitFailed](#m_binitfailed)|Proměnná, která určuje, zda modul Inicializace selhala.|

## <a name="remarks"></a>Poznámky

Instance `CAtlBaseModule` pojmenované _AtlBaseModule je k dispozici ve všech projektech ATL obsahuje popisovač instance modulu, popisovač pro modul, který obsahuje prostředky (která je ve výchozím nastavení, je jeden a tentýž) a pole popisovačů pro moduly, které poskytuje primární prostředky. `CAtlBaseModule` můžete bezpečně přistupovat z více vláken.

Nahradí tato třída zastaralá [ccommodule –](../../atl/reference/ccommodule-class.md) třída používaná v dřívějších verzích ATL.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)

`CAtlBaseModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

##  <a name="addresourceinstance"></a>  CAtlBaseModule::AddResourceInstance

Přidá instanci prostředku do seznamu uložených obslužné rutiny.

```
bool AddResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parametry

*hInst*<br/>
Instance prostředku pro přidání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud prostředek byl úspěšně přidán, false v opačném případě.

##  <a name="catlbasemodule"></a>  CAtlBaseModule::CAtlBaseModule

Konstruktor

```
CAtlBaseModule() throw();
```

### <a name="remarks"></a>Poznámky

Vytvoří `CAtlBaseModule`.

##  <a name="gethinstanceat"></a>  CAtlBaseModule::GetHInstanceAt

Vrátí popisovač do instance zadaného prostředku.

```
HINSTANCE GetHInstanceAt(int i) throw();
```

### <a name="parameters"></a>Parametry

*i*<br/>
Počet instancí prostředku.

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač instance prostředku nebo hodnota NULL, pokud neexistuje žádný odpovídající instance prostředku.

##  <a name="getmoduleinstance"></a>  CAtlBaseModule::GetModuleInstance

Vrátí instanci modulu z `CAtlBaseModule` objektu.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí instanci modulu.

##  <a name="getresourceinstance"></a>  CAtlBaseModule::GetResourceInstance

Vrátí instanci zdroje.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí instanci zdroje.

##  <a name="m_binitfailed"></a>  CAtlBaseModule::m_bInitFailed

Proměnná, která určuje, zda modul Inicializace selhala.

```
static bool m_bInitFailed;
```

### <a name="remarks"></a>Poznámky

True, pokud modul inicializován, false Pokud jí nepovedlo inicializovat.

##  <a name="removeresourceinstance"></a>  CAtlBaseModule::RemoveResourceInstance

Odebere instanci prostředků ze seznamu uložených obslužné rutiny.

```
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parametry

*hInst*<br/>
Instance prostředku pro odebrání.

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud prostředek byl úspěšně odebrán, false, jinak.

##  <a name="setresourceinstance"></a>  CAtlBaseModule::SetResourceInstance

Nastaví instance prostředku `CAtlBaseModule` objektu.

```
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parametry

*hInst*<br/>
Nová instance prostředku.

### <a name="return-value"></a>Návratová hodnota

Vrátí instanci aktualizovaný prostředek.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
