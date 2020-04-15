---
title: CReversalTransition – třída
ms.date: 11/04/2016
f1_keywords:
- CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::Create
- AFXANIMATIONCONTROLLER/CReversalTransition::m_duration
helpviewer_keywords:
- CReversalTransition [MFC], CReversalTransition
- CReversalTransition [MFC], Create
- CReversalTransition [MFC], m_duration
ms.assetid: e89516be-2d07-4885-95a8-fc278f46e3ad
ms.openlocfilehash: 73d12fb6bbaefcfac1437248ebe11f3a5c24c45b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368320"
---
# <a name="creversaltransition-class"></a>CReversalTransition – třída

Zapouzdřuje obrácený přechod.

## <a name="syntax"></a>Syntaxe

```
class CReversalTransition : public CBaseTransition;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CReversalTransition::CReversalTransition](#creversaltransition)|Vytvoří objekt obráceného přechodu a inicializuje jeho trvání.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CReversalTransition::Vytvořit](#create)|Volá knihovnu přechodu k vytvoření zapouzdřený přechod ový objekt COM. (Přepíše [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CReversalTransitionTransition::m_duration](#m_duration)|Doba trvání přechodu.|

## <a name="remarks"></a>Poznámky

Obrácení přechodu hladce mění směr v průběhu dané doby trvání. Konečná hodnota bude stejná jako počáteční hodnota a konečná rychlost bude záporná počáteční rychlosti. Vzhledem k tomu, že všechny přechody jsou vymazány automaticky, doporučuje se jim přidělit pomocí operátoru new. Zapouzdřený objekt IUIAnimationTransition COM je vytvořen CAnimationController::AnimateGroup, do té doby je null. Změna členských proměnných po vytvoření tohoto objektu COM nemá žádný vliv.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CReversalTransitionTransition](../../mfc/reference/creversaltransition-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="creversaltransitioncreate"></a><a name="create"></a>CReversalTransition::Vytvořit

Volá knihovnu přechodu k vytvoření zapouzdřený přechod ový objekt COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parametry

*pKnihovna*<br/>
Ukazatel na knihovnu přechodů, která je zodpovědná za vytváření standardních přechodů.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je přechod úspěšně vytvořen; jinak FALSE.

## <a name="creversaltransitioncreversaltransition"></a><a name="creversaltransition"></a>CReversalTransition::CReversalTransition

Vytvoří objekt obráceného přechodu a inicializuje jeho trvání.

```
CReversalTransition(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
Doba trvání přechodu.

## <a name="creversaltransitionm_duration"></a><a name="m_duration"></a>CReversalTransitionTransition::m_duration

Doba trvání přechodu.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
