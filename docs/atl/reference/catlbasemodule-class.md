---
title: CAtlBaseModule – třída
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
ms.openlocfilehash: d57d6e631cb287496a4ff5516e97e65ec0152e30
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168290"
---
# <a name="catlbasemodule-class"></a>CAtlBaseModule – třída

Tato třída je vytvořena v každém projektu ATL.

## <a name="syntax"></a>Syntaxe

```cpp
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
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|Přidá instanci prostředku do seznamu uložených popisovačů.|
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|Vrátí popisovač k zadané instanci prostředku.|
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|Vrátí instanci modulu z `CAtlBaseModule` objektu.|
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|Vrátí instanci prostředku z `CAtlBaseModule` objektu.|
|[CAtlBaseModule::RemoveResourceInstance](#removeresourceinstance)|Odebere instanci prostředku ze seznamu uložených popisovačů.|
|[CAtlBaseModule::SetResourceInstance](#setresourceinstance)|Nastaví instanci prostředku `CAtlBaseModule` objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CAtlBaseModule:: m_bInitFailed](#m_binitfailed)|Proměnná, která označuje, zda se inicializace modulu nezdařila.|

## <a name="remarks"></a>Poznámky

Instance `CAtlBaseModule` pojmenovaného _AtlBaseModule se nachází v každém projektu ATL, který obsahuje popisovač instance modulu, popisovač modulu obsahujícího prostředky (ve výchozím nastavení je to jedna a stejná) a pole popisovačů pro moduly, které poskytují primární prostředky. `CAtlBaseModule`lze bezpečně použít z více vláken.

Tato třída nahrazuje zastaralou třídu [CComModule](../../atl/reference/ccommodule-class.md) , která se používá v dřívějších verzích knihovny ATL.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)

`CAtlBaseModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore. h

## <a name="catlbasemoduleaddresourceinstance"></a><a name="addresourceinstance"></a>CAtlBaseModule::AddResourceInstance

Přidá instanci prostředku do seznamu uložených popisovačů.

```cpp
bool AddResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parametry

*hInst*<br/>
Instance prostředku, která se má přidat

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud byl prostředek úspěšně přidán, jinak false.

## <a name="catlbasemodulecatlbasemodule"></a><a name="catlbasemodule"></a>CAtlBaseModule::CAtlBaseModule

Konstruktor

```cpp
CAtlBaseModule() throw();
```

### <a name="remarks"></a>Poznámky

Vytvoří `CAtlBaseModule`.

## <a name="catlbasemodulegethinstanceat"></a><a name="gethinstanceat"></a>CAtlBaseModule::GetHInstanceAt

Vrátí popisovač k zadané instanci prostředku.

```cpp
HINSTANCE GetHInstanceAt(int i) throw();
```

### <a name="parameters"></a>Parametry

*došlo*<br/>
Číslo instance prostředku

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač instance prostředku nebo hodnotu NULL, pokud neexistuje žádná odpovídající instance prostředku.

## <a name="catlbasemodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CAtlBaseModule::GetModuleInstance

Vrátí instanci modulu z `CAtlBaseModule` objektu.

```cpp
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí instanci modulu.

## <a name="catlbasemodulegetresourceinstance"></a><a name="getresourceinstance"></a>CAtlBaseModule::GetResourceInstance

Vrátí instanci prostředku.

```cpp
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí instanci prostředku.

## <a name="catlbasemodulem_binitfailed"></a><a name="m_binitfailed"></a>CAtlBaseModule:: m_bInitFailed

Proměnná, která označuje, zda se inicializace modulu nezdařila.

```cpp
static bool m_bInitFailed;
```

### <a name="remarks"></a>Poznámky

True, pokud je modul inicializovaný, false, pokud se nepovedlo inicializovat.

## <a name="catlbasemoduleremoveresourceinstance"></a><a name="removeresourceinstance"></a>CAtlBaseModule::RemoveResourceInstance

Odebere instanci prostředku ze seznamu uložených popisovačů.

```cpp
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parametry

*hInst*<br/>
Instance prostředku, která se má odebrat

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud byl prostředek úspěšně odebrán, jinak false.

## <a name="catlbasemodulesetresourceinstance"></a><a name="setresourceinstance"></a>CAtlBaseModule::SetResourceInstance

Nastaví instanci prostředku `CAtlBaseModule` objektu.

```cpp
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
