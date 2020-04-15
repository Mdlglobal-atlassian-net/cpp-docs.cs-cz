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
ms.openlocfilehash: 2a32ee7921e927e25a5196d38c8f5ae350ab2b8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375660"
---
# <a name="cdiscretetransition-class"></a>CDiscreteTransition – třída

Zapouzdřuje diskrétní přechod.

## <a name="syntax"></a>Syntaxe

```
class CDiscreteTransition : public CBaseTransition;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CDiskrétníPřechod::CDiscreteTransition](#cdiscretetransition)|Vytvoří diskrétní objekt přechodu a inicializuje jeho parametry.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDiskrétníPřechod::Vytvořit](#create)|Volá knihovnu přechodu k vytvoření zapouzdřený přechod ový objekt COM. (Přepíše [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CDiskrétníPřechod::m_dblFinalValue](#m_dblfinalvalue)|Hodnota proměnné animace na konci přechodu.|
|[CDiskrétníPřechod::m_delay](#m_delay)|Doba, o kterou má být okamžitý přepínač na konečnou hodnotu odložen.|
|[CDiskrétníPřechod::m_hold](#m_hold)|Doba, o kterou má být proměnná držet konečnou hodnotu.|

## <a name="remarks"></a>Poznámky

Během diskrétního přechodu zůstává proměnná animace na počáteční hodnotě po určitou dobu zpoždění, poté se okamžitě přepne na zadanou konečnou hodnotu a zůstane na této hodnotě po určitou dobu blokování. Vzhledem k tomu, že všechny přechody jsou vymazány automaticky, doporučuje se jim přidělit pomocí operátoru new. Zapouzdřený objekt IUIAnimationTransition COM je vytvořen CAnimationController::AnimateGroup, do té doby je null. Změna členských proměnných po vytvoření tohoto objektu COM nemá žádný vliv.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CDiskrétnípřechod](../../mfc/reference/cdiscretetransition-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="cdiscretetransitioncdiscretetransition"></a><a name="cdiscretetransition"></a>CDiskrétníPřechod::CDiscreteTransition

Vytvoří diskrétní objekt přechodu a inicializuje jeho parametry.

```
CDiscreteTransition(
    UI_ANIMATION_SECONDS delay,
    DOUBLE dblFinalValue,
    UI_ANIMATION_SECONDS hold);
```

### <a name="parameters"></a>Parametry

*Zpoždění*<br/>
Doba, o kterou má být okamžitý přepínač na konečnou hodnotu odložen.

*dblFinalValue*<br/>
Hodnota proměnné animace na konci přechodu.

*Držet*<br/>
Doba, o kterou má být proměnná držet konečnou hodnotu.

## <a name="cdiscretetransitioncreate"></a><a name="create"></a>CDiskrétníPřechod::Vytvořit

Volá knihovnu přechodu k vytvoření zapouzdřený přechod ový objekt COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

*pKnihovna*<br/>
Ukazatel na [rozhraní IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), které definuje knihovnu standardních přechodů.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je přechod úspěšně vytvořen; jinak FALSE.

## <a name="cdiscretetransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>CDiskrétníPřechod::m_dblFinalValue

Hodnota proměnné animace na konci přechodu.

```
DOUBLE m_dblFinalValue;
```

## <a name="cdiscretetransitionm_delay"></a><a name="m_delay"></a>CDiskrétníPřechod::m_delay

Doba, o kterou má být okamžitý přepínač na konečnou hodnotu odložen.

```
UI_ANIMATION_SECONDS m_delay;
```

## <a name="cdiscretetransitionm_hold"></a><a name="m_hold"></a>CDiskrétníPřechod::m_hold

Doba, o kterou má být proměnná držet konečnou hodnotu.

```
UI_ANIMATION_SECONDS m_hold;
```

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
