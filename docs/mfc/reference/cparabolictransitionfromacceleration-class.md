---
title: Třída CParabolicTransitionFromAcceleration
ms.date: 11/04/2016
f1_keywords:
- CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::Create
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblFinalVelocity
helpviewer_keywords:
- CParabolicTransitionFromAcceleration [MFC], CParabolicTransitionFromAcceleration
- CParabolicTransitionFromAcceleration [MFC], Create
- CParabolicTransitionFromAcceleration [MFC], m_dblAcceleration
- CParabolicTransitionFromAcceleration [MFC], m_dblFinalValue
- CParabolicTransitionFromAcceleration [MFC], m_dblFinalVelocity
ms.assetid: 1e59b86f-358b-4da0-a4fd-8eaf5e85e00f
ms.openlocfilehash: 0aa5831e2262602ee46bd69031e5927a86b978e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364091"
---
# <a name="cparabolictransitionfromacceleration-class"></a>Třída CParabolicTransitionFromAcceleration

Zapouzdřuje přechod parabolického zrychlení.

## <a name="syntax"></a>Syntaxe

```
class CParabolicTransitionFromAcceleration : public CBaseTransition;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration](#cparabolictransitionfromacceleration)|Vytvoří přechod parabolického zrychlení a inicializuje jej se zadanými parametry.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration::Vytvořit](#create)|Volá knihovnu přechodu k vytvoření zapouzdřený přechod ový objekt COM. (Přepíše [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration::m_dblAcceleration](#m_dblacceleration)|Zrychlení proměnné animace během přechodu.|
|[CParabolicTransitionFromAcceleration::m_dblFinalValue](#m_dblfinalvalue)|Hodnota proměnné animace na konci přechodu.|
|[CParabolicTransitionFromAcceleration::m_dblFinalVelocity](#m_dblfinalvelocity)|Rychlost proměnné animace na konci přechodu.|

## <a name="remarks"></a>Poznámky

Během parabolického akceleračního přechodu se hodnota proměnné animace změní z počáteční hodnoty na konečnou hodnotu končící zadanou rychlostí. Zadáním rychlosti zrychlení můžete určit, jak rychle proměnná dosáhne konečné hodnoty. Vzhledem k tomu, že všechny přechody jsou vymazány automaticky, doporučuje se jim přidělit pomocí operátoru new. Zapouzdřený objekt IUIAnimationTransition COM je vytvořen CAnimationController::AnimateGroup, do té doby je null. Změna členských proměnných po vytvoření tohoto objektu COM nemá žádný vliv.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CParabolicTransitionFromAcceleration](../../mfc/reference/cparabolictransitionfromacceleration-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="cparabolictransitionfromaccelerationcparabolictransitionfromacceleration"></a><a name="cparabolictransitionfromacceleration"></a>CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration

Vytvoří přechod parabolického zrychlení a inicializuje jej se zadanými parametry.

```
CParabolicTransitionFromAcceleration(
    DOUBLE dblFinalValue,
    DOUBLE dblFinalVelocity,
    DOUBLE dblAcceleration);
```

### <a name="parameters"></a>Parametry

*dblFinalValue*<br/>
Hodnota proměnné animace na konci přechodu.

*dblFinalVelocity*<br/>
Rychlost proměnné animace na konci přechodu.

*akcelerace dBL*<br/>
Zrychlení proměnné animace během přechodu.

## <a name="cparabolictransitionfromaccelerationcreate"></a><a name="create"></a>CParabolicTransitionFromAcceleration::Vytvořit

Volá knihovnu přechodu k vytvoření zapouzdřený přechod ový objekt COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* /* not used */);
```

### <a name="parameters"></a>Parametry

*pKnihovna*<br/>
Ukazatel na knihovnu přechodů, která je zodpovědná za vytváření standardních přechodů.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je přechod úspěšně vytvořen; jinak FALSE.

## <a name="cparabolictransitionfromaccelerationm_dblacceleration"></a><a name="m_dblacceleration"></a>CParabolicTransitionFromAcceleration::m_dblAcceleration

Zrychlení proměnné animace během přechodu.

```
DOUBLE m_dblAcceleration;
```

## <a name="cparabolictransitionfromaccelerationm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>CParabolicTransitionFromAcceleration::m_dblFinalValue

Hodnota proměnné animace na konci přechodu.

```
DOUBLE m_dblFinalValue;
```

## <a name="cparabolictransitionfromaccelerationm_dblfinalvelocity"></a><a name="m_dblfinalvelocity"></a>CParabolicTransitionFromAcceleration::m_dblFinalVelocity

Rychlost proměnné animace na konci přechodu.

```
DOUBLE m_dblFinalVelocity;
```

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
