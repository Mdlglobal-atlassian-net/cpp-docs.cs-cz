---
title: Cwintraitsor – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
dev_langs:
- C++
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48303c6115ac1d2314e3038556b8f98330a6182e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062667"
---
# <a name="cwintraitsor-class"></a>Cwintraitsor – třída

Tato třída poskytuje metody pro standardizaci stylů použitých při vytváření objektu okno.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

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
Rozšířené styly oken ve výchozím nastavení.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|Načte rozšířené styly `CWinTraitsOR` objektu.|
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|Načte standardní styly `CWinTraitsOR` objektu.|

## <a name="remarks"></a>Poznámky

To [vlastností okna](../../atl/understanding-window-traits.md) třída poskytuje jednoduchý způsob pro standardizaci stylů použitých pro vytvoření objektu ATL okna. Použít jako parametr šablony specializace této třídy [CWindowImpl](../../atl/reference/cwindowimpl-class.md) nebo jiného tříd oken ATL k určení minimální sadu standardní a rozšířené stylů se použije pro instance této třídy okna.

Pokud chcete mít jistotu, že určité styly jsou nastavené pro všechny instance třídy okna při povolení další styly nastavení na základě jednotlivé instance při volání funkce použijte specializace této šablony [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create).

Pokud chcete zadat výchozí styly oken, které budou použity pouze v případě, že žádné další styly jsou zadány při volání funkce `CWindowImpl::Create`, použijte [cwintraits –](../../atl/reference/cwintraits-class.md) místo.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="getwndstyle"></a>  CWinTraitsOR::GetWndStyle

Voláním této funkce načtete kombinace standardní stylů (pomocí logického operátoru OR) `CWinTraits` objektu a výchozí styly určené *t_dwStyle*.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Stylů použitých pro vytvoření okna.

### <a name="return-value"></a>Návratová hodnota

Kombinace stylů, které jsou předány v *dwStyle* a ve výchozím nastavení těch, které jsou určené `t_dwStyle`, pomocí logického operátoru OR.

##  <a name="getwndexstyle"></a>  CWinTraitsOR::GetWndExStyle

Voláním této funkce načtete kombinace rozšířené styly (pomocí logického operátoru OR) `CWinTraits` objektu a výchozí styly určené `t_dwStyle`.

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>Parametry

*dwExStyle*<br/>
Rozšířené stylů použitých pro vytvoření okna.

### <a name="return-value"></a>Návratová hodnota

Rozšířené styly, které jsou předány v kombinaci *dwExStyle* a těch, které jsou určené výchozí `t_dwExStyle`, pomocí logického operátoru OR

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[Principy vlastností okna](../../atl/understanding-window-traits.md)

