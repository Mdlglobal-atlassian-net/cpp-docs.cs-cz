---
title: Třída CWinTraits
ms.date: 11/04/2016
f1_keywords:
- CWinTraits
- ATLWIN/ATL::CWinTraits
- ATLWIN/ATL::CWinTraits::GetWndExStyle
- ATLWIN/ATL::CWinTraits::GetWndStyle
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
ms.openlocfilehash: fd73f733e4eff21da92937d1e1b0cce21552a48c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330301"
---
# <a name="cwintraits-class"></a>Třída CWinTraits

Tato třída poskytuje metodu pro standardizaci stylů používaných při vytváření objektu okna.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```

#### <a name="parameters"></a>Parametry

*t_dwStyle*<br/>
Výchozí standardní styly oken.

*t_dwExStyle*<br/>
Výchozí styly rozšířených oken.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CWinTraits::GetWndExStyle](#getwndexstyle)|(Statické) Načte rozšířené styly `CWinTraits` pro objekt.|
|[CWinTraits::GetWndStyle](#getwndstyle)|(Statické) Načte standardní styly `CWinTraits` pro objekt.|

## <a name="remarks"></a>Poznámky

Tato třída [vlastností okna](../../atl/understanding-window-traits.md) poskytuje jednoduchou metodu pro standardizaci stylů použitých pro vytvoření objektu okna KNIHOVNY ATL. Použijte specializaci této třídy jako parametr šablony [cWindowImpl](../../atl/reference/cwindowimpl-class.md) nebo jiné třídy oken knihovny ATL k určení výchozího standardního a rozšířeného stylu používaného pro instance této třídy okna.

Tuto šablonu použijte, pokud chcete poskytnout výchozí styly oken, které budou použity pouze v případě, že ve volání [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)nejsou zadány žádné jiné styly.

Knihovna ATL poskytuje tři předdefinované specializace této šablony pro běžně používané kombinace stylů oken:

- `CControlWinTraits`

   Navrženo pro standardní ovládací okno. Používají se následující standardní styly: WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN a WS_CLIPSIBLINGS. Neexistují žádné rozšířené styly.

- `CFrameWinTraits`

   Navrženo pro standardní okno rámu. Mezi použité standardní styly patří: WS_OVERLAPPEDWINDOW, WS_CLIPCHILDREN a WS_CLIPSIBLINGS. Mezi použité rozšířené styly patří: WS_EX_APPWINDOW a WS_EX_WINDOWEDGE.

- `CMDIChildWinTraits`

   Navrženo pro standardní podřízené okno MDI. Mezi používané standardní styly patří: WS_OVERLAPPEDWINDOW, WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN a WS_CLIPSIBLINGS. Rozšířené styly používané patří: WS_EX_MDICHILD.

Pokud chcete zajistit, že některé styly jsou nastaveny pro všechny instance třídy okna a zároveň umožňuje jiné styly, které mají být nastaveny na základě instance, použijte [CWinTraitsOR](../../atl/reference/cwintraitsor-class.md) místo.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="cwintraitsgetwndstyle"></a><a name="getwndstyle"></a>CWinTraits::GetWndStyle

Volání této funkce načíst standardní `CWinTraits` styly objektu.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Standardní styly používané pro vytvoření okna. Pokud *je dwStyle* 0, jsou`t_dwStyle`vráceny hodnoty stylu šablony ( ). Pokud *dwStyle* je nenulová, *dwStyle* je vrácena.

### <a name="return-value"></a>Návratová hodnota

Standardní styly oken objektu.

## <a name="cwintraitsgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraits::GetWndExStyle

Volání této funkce načíst rozšířené `CWinTraits` styly objektu.

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>Parametry

*dwExStyl*<br/>
Rozšířené styly používané pro vytvoření okna. Pokud *je dwExStyle* 0, jsou`t_dwExStyle`vráceny hodnoty stylu šablony ( ). Pokud *dwExStyle* je nenulová, *dwExStyle* je vrácena.

### <a name="return-value"></a>Návratová hodnota

Rozšířené styly oken objektu.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Principy vlastností okna](../../atl/understanding-window-traits.md)
