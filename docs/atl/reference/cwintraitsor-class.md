---
title: Třída CWinTraitsOR
ms.date: 11/04/2016
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
ms.openlocfilehash: 825f79190c6f68cd1372154e4e02f430f545aa48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330285"
---
# <a name="cwintraitsor-class"></a>Třída CWinTraitsOR

Tato třída poskytuje metodu pro standardizaci stylů používaných při vytváření objektu okna.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0,
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
```

#### <a name="parameters"></a>Parametry

*t_dwStyle*<br/>
Výchozí styly oken.

*t_dwExStyle*<br/>
Výchozí styly rozšířených oken.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|Načte rozšířené styly `CWinTraitsOR` pro objekt.|
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|Načte standardní styly `CWinTraitsOR` pro objekt.|

## <a name="remarks"></a>Poznámky

Tato třída [vlastností okna](../../atl/understanding-window-traits.md) poskytuje jednoduchou metodu pro standardizaci stylů použitých pro vytvoření objektu okna KNIHOVNY ATL. Použijte specializaci této třídy jako parametr šablony [cWindowImpl](../../atl/reference/cwindowimpl-class.md) nebo jiné třídy okna knihovny ATL k určení minimální sady standardních a rozšířených stylů, které mají být použity pro instance této třídy okna.

Specializaci této šablony použijte, pokud chcete zajistit, aby byly určité styly nastaveny pro všechny instance třídy okna a zároveň povolit, aby byly jiné styly nastaveny na základě instance ve volání [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create).

Pokud chcete poskytnout výchozí styly oken, které budou použity pouze `CWindowImpl::Create`v případě, že žádné jiné styly jsou určeny ve volání , použijte [CWinTraits](../../atl/reference/cwintraits-class.md) místo.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="cwintraitsorgetwndstyle"></a><a name="getwndstyle"></a>CWinTraitsOR::GetWndStyle

Voláním této funkce načtěte kombinaci (pomocí logického `CWinTraits` operátoru OR) standardních stylů objektu a výchozích stylů určených *t_dwStyle*.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Styly používané pro vytvoření okna.

### <a name="return-value"></a>Návratová hodnota

Kombinace stylů, které jsou předány v *dwStyle* `t_dwStyle`a výchozí ty určené , pomocí logické ho operátoru OR.

## <a name="cwintraitsorgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraitsOR::GetWndExStyle

Voláním této funkce načtěte kombinaci (pomocí logického `CWinTraits` operátoru OR) rozšířených stylů objektu a výchozích stylů určených písmenem `t_dwStyle`.

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>Parametry

*dwExStyl*<br/>
Rozšířené styly používané pro vytvoření okna.

### <a name="return-value"></a>Návratová hodnota

Kombinace rozšířených stylů, které jsou předány v *dwExStyle* a výchozí ty určené `t_dwExStyle`, pomocí logické operátor OR

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Principy vlastností okna](../../atl/understanding-window-traits.md)
