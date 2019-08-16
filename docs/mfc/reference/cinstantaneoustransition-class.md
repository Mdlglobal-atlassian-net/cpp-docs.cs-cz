---
title: CInstantaneousTransition – třída
ms.date: 11/04/2016
f1_keywords:
- CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::Create
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::m_dblFinalValue
helpviewer_keywords:
- CInstantaneousTransition [MFC], CInstantaneousTransition
- CInstantaneousTransition [MFC], Create
- CInstantaneousTransition [MFC], m_dblFinalValue
ms.assetid: c3d5121f-2c6b-4221-9e57-10e082a31120
ms.openlocfilehash: f3861bbbc0fc138dcb0f2a8b969ed9bde41335bd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505940"
---
# <a name="cinstantaneoustransition-class"></a>CInstantaneousTransition – třída

Zapouzdřuje okamžitý přechod.

## <a name="syntax"></a>Syntaxe

```
class CInstantaneousTransition : public CBaseTransition;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CInstantaneousTransition::CInstantaneousTransition](#cinstantaneoustransition)|Vytvoří objekt přechodu a inicializuje jeho konečnou hodnotu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CInstantaneousTransition:: Create](#create)|Volá knihovnu přechodu k vytvoření zapouzdřeného přechodu objektu COM. (Overrides [CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CInstantaneousTransition::m_dblFinalValue](#m_dblfinalvalue)|Hodnota proměnné animace na konci přechodu.|

## <a name="remarks"></a>Poznámky

Během okamžitého přechodu se hodnota proměnné animace okamžitě změní z aktuální hodnoty na zadanou konečnou hodnotu. Doba trvání tohoto přechodu je vždycky nulová. Vzhledem k tomu, že jsou všechny přechody vymazány automaticky, doporučujeme je přidělit pomocí operátoru new. Zapouzdřený objekt COM IUIAnimationTransition je vytvořen pomocí CAnimationController:: Animate, dokud nebude NULL. Změna členských proměnných po vytvoření tohoto objektu COM nemá žádný vliv.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CInstantaneousTransition](../../mfc/reference/cinstantaneoustransition-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller. h

##  <a name="cinstantaneoustransition"></a>CInstantaneousTransition::CInstantaneousTransition

Vytvoří objekt přechodu a inicializuje jeho konečnou hodnotu.

```
CInstantaneousTransition(DOUBLE dblFinalValue);
```

### <a name="parameters"></a>Parametry

*dblFinalValue*<br/>
Hodnota proměnné animace na konci přechodu.

##  <a name="create"></a>CInstantaneousTransition:: Create

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

##  <a name="m_dblfinalvalue"></a>CInstantaneousTransition::m_dblFinalValue

Hodnota proměnné animace na konci přechodu.

```
DOUBLE m_dblFinalValue;
```

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
