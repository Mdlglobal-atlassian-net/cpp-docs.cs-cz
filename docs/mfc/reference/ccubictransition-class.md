---
title: CCubicTransition – třída
ms.date: 11/04/2016
f1_keywords:
- CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::Create
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalVelocity
- AFXANIMATIONCONTROLLER/CCubicTransition::m_duration
helpviewer_keywords:
- CCubicTransition [MFC], CCubicTransition
- CCubicTransition [MFC], Create
- CCubicTransition [MFC], m_dblFinalValue
- CCubicTransition [MFC], m_dblFinalVelocity
- CCubicTransition [MFC], m_duration
ms.assetid: 4fc30e9c-160c-45e1-bdbe-51adf8fee9c5
ms.openlocfilehash: b6bb626f944ce87748809a5eb03a6f06f92c3de5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507143"
---
# <a name="ccubictransition-class"></a>CCubicTransition – třída

Zapouzdřuje přechod krychle.

## <a name="syntax"></a>Syntaxe

```
class CCubicTransition : public CBaseTransition;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CCubicTransition::CCubicTransition](#ccubictransition)|Vytvoří objekt přechodu a inicializuje jeho parametry.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CCubicTransition:: Create](#create)|Volá knihovnu přechodu k vytvoření zapouzdřeného přechodu objektu COM. (Overrides [CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CCubicTransition::m_dblFinalValue](#m_dblfinalvalue)|Hodnota proměnné animace na konci přechodu.|
|[CCubicTransition::m_dblFinalVelocity](#m_dblfinalvelocity)|Rychlost proměnné na konci přechodu.|
|[CCubicTransition::m_duration](#m_duration)|Doba trvání přechodu.|

## <a name="remarks"></a>Poznámky

Během přechodu krychle se hodnota proměnné animace mění z původní hodnoty na zadanou konečnou hodnotu po dobu trvání přechodu a končí zadanou rychlostí. Vzhledem k tomu, že jsou všechny přechody vymazány automaticky, doporučujeme je přidělit pomocí operátoru new. Zapouzdřený objekt COM IUIAnimationTransition je vytvořen pomocí CAnimationController:: Animate, dokud nebude NULL. Změna členských proměnných po vytvoření tohoto objektu COM nemá žádný vliv.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCubicTransition`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller. h

##  <a name="ccubictransition"></a>CCubicTransition::CCubicTransition

Vytvoří objekt přechodu a inicializuje jeho parametry.

```
CCubicTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE finalVelocity);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
Doba trvání přechodu.

*finalValue*<br/>
Hodnota proměnné animace na konci přechodu.

*finalVelocity*<br/>
Rychlost proměnné na konci přechodu.

##  <a name="create"></a>CCubicTransition:: Create

Volá knihovnu přechodu k vytvoření zapouzdřeného přechodu objektu COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parametry

*pLibrary*<br/>
Ukazatel na [rozhraní IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), které definuje knihovnu standardních přechodů.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je převod úspěšně vytvořen; v opačném případě FALSE.

##  <a name="m_dblfinalvalue"></a>CCubicTransition::m_dblFinalValue

Hodnota proměnné animace na konci přechodu.

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_dblfinalvelocity"></a>CCubicTransition::m_dblFinalVelocity

Rychlost proměnné na konci přechodu.

```
DOUBLE m_dblFinalVelocity;
```

##  <a name="m_duration"></a>CCubicTransition::m_duration

Doba trvání přechodu.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
