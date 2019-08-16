---
title: CDiscreteTransition – třída
ms.date: 11/04/2016
f1_keywords:
- CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::Create
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_delay
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_hold
helpviewer_keywords:
- CDiscreteTransition [MFC], CDiscreteTransition
- CDiscreteTransition [MFC], Create
- CDiscreteTransition [MFC], m_dblFinalValue
- CDiscreteTransition [MFC], m_delay
- CDiscreteTransition [MFC], m_hold
ms.assetid: b4d84fb3-ccaa-451c-a69b-6b50dcb9b9c8
ms.openlocfilehash: 7087dfa13972737f0a1244d2cc9a7088b23dc184
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506855"
---
# <a name="cdiscretetransition-class"></a>CDiscreteTransition – třída

Zapouzdřuje diskrétní přechod.

## <a name="syntax"></a>Syntaxe

```
class CDiscreteTransition : public CBaseTransition;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CDiscreteTransition::CDiscreteTransition](#cdiscretetransition)|Vytvoří diskrétní objekt přechodu a inicializuje jeho parametry.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CDiscreteTransition:: Create](#create)|Volá knihovnu přechodu k vytvoření zapouzdřeného přechodu objektu COM. (Overrides [CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CDiscreteTransition::m_dblFinalValue](#m_dblfinalvalue)|Hodnota proměnné animace na konci přechodu.|
|[CDiscreteTransition::m_delay](#m_delay)|Doba, po kterou se má zpozdit okamžitý přepínač na konečnou hodnotu.|
|[CDiscreteTransition::m_hold](#m_hold)|Doba, po kterou se má proměnná uchovávat v konečné hodnotě.|

## <a name="remarks"></a>Poznámky

Během diskrétního přechodu zůstane proměnná animace na počáteční hodnotě pro zadanou dobu zpoždění a pak se okamžitě přepne na zadanou konečnou hodnotu a zůstane v této hodnotě pro danou dobu uchování. Vzhledem k tomu, že jsou všechny přechody vymazány automaticky, doporučujeme je přidělit pomocí operátoru new. Zapouzdřený objekt COM IUIAnimationTransition je vytvořen pomocí CAnimationController:: Animate, dokud nebude NULL. Změna členských proměnných po vytvoření tohoto objektu COM nemá žádný vliv.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CDiscreteTransition](../../mfc/reference/cdiscretetransition-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller. h

##  <a name="cdiscretetransition"></a>CDiscreteTransition::CDiscreteTransition

Vytvoří diskrétní objekt přechodu a inicializuje jeho parametry.

```
CDiscreteTransition(
    UI_ANIMATION_SECONDS delay,
    DOUBLE dblFinalValue,
    UI_ANIMATION_SECONDS hold);
```

### <a name="parameters"></a>Parametry

*delay*<br/>
Doba, po kterou se má zpozdit okamžitý přepínač na konečnou hodnotu.

*dblFinalValue*<br/>
Hodnota proměnné animace na konci přechodu.

*čekání*<br/>
Doba, po kterou se má proměnná uchovávat v konečné hodnotě.

##  <a name="create"></a>CDiscreteTransition:: Create

Volá knihovnu přechodu k vytvoření zapouzdřeného přechodu objektu COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

*pLibrary*<br/>
Ukazatel na [rozhraní IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), které definuje knihovnu standardních přechodů.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je převod úspěšně vytvořen; v opačném případě FALSE.

##  <a name="m_dblfinalvalue"></a>CDiscreteTransition::m_dblFinalValue

Hodnota proměnné animace na konci přechodu.

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_delay"></a>CDiscreteTransition::m_delay

Doba, po kterou se má zpozdit okamžitý přepínač na konečnou hodnotu.

```
UI_ANIMATION_SECONDS m_delay;
```

##  <a name="m_hold"></a>CDiscreteTransition::m_hold

Doba, po kterou se má proměnná uchovávat v konečné hodnotě.

```
UI_ANIMATION_SECONDS m_hold;
```

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
