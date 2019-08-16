---
title: CAccelerateDecelerateTransition – třída
ms.date: 11/04/2016
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
ms.openlocfilehash: 1e55e81b4d9b5c324f86bfd141b74d9faa362d94
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507744"
---
# <a name="cacceleratedeceleratetransition-class"></a>CAccelerateDecelerateTransition – třída

Implementuje přechod zrychlit zpomalení.

## <a name="syntax"></a>Syntaxe

```
class CAccelerateDecelerateTransition : public CBaseTransition;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|Vytvoří objekt přechodu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CAccelerateDecelerateTransition:: Create](#create)|Volá knihovnu přechodu k vytvoření zapouzdřeného přechodu objektu COM. (Overrides [CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|Poměr doby strávené zrychlením na dobu trvání.|
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|Poměr času stráveného zpomalením doby trvání.|
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|Doba trvání přechodu.|
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|Hodnota proměnné animace na konci přechodu.|

## <a name="remarks"></a>Poznámky

Při přechodu zrychlit zpomalení se proměnná animace zrychlí a pak zpomaluje po celou dobu trvání přechodu a končí zadanou hodnotou. Můžete určit, jak rychle proměnná zrychlí a zpomaluje nezávisle, zadáním různých poměrů zrychlení a zpomalení. Když je počáteční rychlost nula, poměr zrychlení je zlomek doby trvání, po kterou bude mít tato proměnná útratu zrychlení. Podobně jako poměr zpomalení. Pokud je počáteční rychlost nenulová, je to zlomek času mezi rychlostí dosáhne nuly a koncem přechodu. Poměr zrychlení a poměr zpomalení by měl být platný maximálně 1,0. Vzhledem k tomu, že jsou všechny přechody vymazány automaticky, doporučujeme je přidělit pomocí operátoru new. Zapouzdřený objekt COM IUIAnimationTransition je vytvořen pomocí CAnimationController:: Animate, dokud nebude NULL. Změna členských proměnných po vytvoření tohoto objektu COM nemá žádný vliv.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CAccelerateDecelerateTransition`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller. h

##  <a name="cacceleratedeceleratetransition"></a>CAccelerateDecelerateTransition::CAccelerateDecelerateTransition

Vytvoří objekt přechodu.

```
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE accelerationRatio = 0.3,
    DOUBLE decelerationRatio = 0.3);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
Doba trvání přechodu.

*finalValue*<br/>
Hodnota proměnné animace na konci přechodu.

*accelerationRatio*<br/>
Poměr doby strávené zrychlením na dobu trvání.

*decelerationRatio*<br/>
Poměr času stráveného zpomalením doby trvání.

##  <a name="create"></a>CAccelerateDecelerateTransition:: Create

Volá knihovnu přechodu k vytvoření zapouzdřeného přechodu objektu COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* *\not used*\);
```

### <a name="parameters"></a>Parametry

*pLibrary*<br/>
Ukazatel na [rozhraní IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), které definuje knihovnu standardních přechodů.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je převod úspěšně vytvořen; v opačném případě FALSE.

##  <a name="m_accelerationratio"></a>CAccelerateDecelerateTransition::m_accelerationRatio

Poměr doby strávené zrychlením na dobu trvání.

```
DOUBLE m_accelerationRatio;
```

##  <a name="m_decelerationratio"></a>CAccelerateDecelerateTransition::m_decelerationRatio

Poměr času stráveného zpomalením doby trvání.

```
DOUBLE m_decelerationRatio;
```

##  <a name="m_duration"></a>CAccelerateDecelerateTransition::m_duration

Doba trvání přechodu.

```
UI_ANIMATION_SECONDS m_duration;
```

##  <a name="m_finalvalue"></a>CAccelerateDecelerateTransition::m_finalValue

Hodnota proměnné animace na konci přechodu.

```
DOUBLE m_finalValue;
```

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
