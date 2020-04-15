---
title: CAccelerateDecelerateTransition – třída
ms.date: 11/04/2016
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
ms.openlocfilehash: 356ba30e6d9a638672d2c356676735ebfaed8f3e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371151"
---
# <a name="cacceleratedeceleratetransition-class"></a>CAccelerateDecelerateTransition – třída

Implementuje přechod zrychlení zpomalit.

## <a name="syntax"></a>Syntaxe

```
class CAccelerateDecelerateTransition : public CBaseTransition;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|Vytvoří objekt přechodu.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAccelerateDecelerateTransition::Vytvořit](#create)|Volá knihovnu přechodu k vytvoření zapouzdřený přechod ový objekt COM. (Přepíše [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|Poměr času stráveného zrychlováním k době trvání.|
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|Poměr času stráveného zpomalením k době trvání.|
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|Doba trvání přechodu.|
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|Hodnota proměnné animace na konci přechodu.|

## <a name="remarks"></a>Poznámky

Během přechodu akcelerace zpomalit proměnné animace zrychluje a pak zpomaluje po dobu trvání přechodu, končící na zadanou hodnotu. Můžete určit, jak rychle se proměnná zrychluje a zpomaluje nezávisle, a to zadáním různých poměrů zrychlení a zpomalení. Pokud je počáteční rychlost nulová, je poměr zrychlení zlomkem doby trvání, kterou proměnná stráví zrychlením; stejně jako poměr zpomalení. Pokud je počáteční rychlost nenulová, jedná se o zlomek doby mezi rychlostí dosahující nuly a koncem přechodu. Poměr zrychlení a poměr zpomalení by se měly sčítat maximálně do hodnoty 1,0. Vzhledem k tomu, že všechny přechody jsou vymazány automaticky, doporučuje se jim přidělit pomocí operátoru new. Zapouzdřený objekt IUIAnimationTransition COM je vytvořen CAnimationController::AnimateGroup, do té doby je null. Změna členských proměnných po vytvoření tohoto objektu COM nemá žádný vliv.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CAccelerateDecelerateTransition`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="cacceleratedeceleratetransitioncacceleratedeceleratetransition"></a><a name="cacceleratedeceleratetransition"></a>CAccelerateDecelerateTransition::CAccelerateDecelerateTransition

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

*Accelerationratio*<br/>
Poměr času stráveného zrychlováním k době trvání.

*Decelerationratio*<br/>
Poměr času stráveného zpomalením k době trvání.

## <a name="cacceleratedeceleratetransitioncreate"></a><a name="create"></a>CAccelerateDecelerateTransition::Vytvořit

Volá knihovnu přechodu k vytvoření zapouzdřený přechod ový objekt COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* *\not used*\);
```

### <a name="parameters"></a>Parametry

*pKnihovna*<br/>
Ukazatel na [rozhraní IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), které definuje knihovnu standardních přechodů.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je přechod úspěšně vytvořen; jinak FALSE.

## <a name="cacceleratedeceleratetransitionm_accelerationratio"></a><a name="m_accelerationratio"></a>CAccelerateDecelerateTransition::m_accelerationRatio

Poměr času stráveného zrychlováním k době trvání.

```
DOUBLE m_accelerationRatio;
```

## <a name="cacceleratedeceleratetransitionm_decelerationratio"></a><a name="m_decelerationratio"></a>CAccelerateDecelerateTransition::m_decelerationRatio

Poměr času stráveného zpomalením k době trvání.

```
DOUBLE m_decelerationRatio;
```

## <a name="cacceleratedeceleratetransitionm_duration"></a><a name="m_duration"></a>CAccelerateDecelerateTransition::m_duration

Doba trvání přechodu.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="cacceleratedeceleratetransitionm_finalvalue"></a><a name="m_finalvalue"></a>CAccelerateDecelerateTransition::m_finalValue

Hodnota proměnné animace na konci přechodu.

```
DOUBLE m_finalValue;
```

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
