---
title: CConstantTransition – třída
ms.date: 11/04/2016
f1_keywords:
- CConstantTransition
- AFXANIMATIONCONTROLLER/CConstantTransition
- AFXANIMATIONCONTROLLER/CConstantTransition::CConstantTransition
- AFXANIMATIONCONTROLLER/CConstantTransition::Create
- AFXANIMATIONCONTROLLER/CConstantTransition::m_duration
helpviewer_keywords:
- CConstantTransition [MFC], CConstantTransition
- CConstantTransition [MFC], Create
- CConstantTransition [MFC], m_duration
ms.assetid: f6fa4780-a71b-4cd6-80aa-d4792ace36c2
ms.openlocfilehash: ccf08b309e64cd82215acb6032bc2a777f4c809a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507158"
---
# <a name="cconstanttransition-class"></a>CConstantTransition – třída

Zapouzdřuje konstantní přechod.

## <a name="syntax"></a>Syntaxe

```
class CConstantTransition : public CBaseTransition;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CConstantTransition::CConstantTransition](#cconstanttransition)|Vytvoří objekt přechodu a inicializuje jeho dobu trvání.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CConstantTransition:: Create](#create)|Volá knihovnu přechodu k vytvoření zapouzdřeného přechodu objektu COM. (Overrides [CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CConstantTransition::m_duration](#m_duration)|Doba trvání přechodu.|

## <a name="remarks"></a>Poznámky

Během konstantního přechodu hodnota proměnné animace zůstane na počáteční hodnotě po dobu trvání přechodu. Vzhledem k tomu, že jsou všechny přechody vymazány automaticky, doporučujeme je přidělit pomocí operátoru new. Zapouzdřený objekt COM IUIAnimationTransition je vytvořen pomocí CAnimationController:: Animate, dokud nebude NULL. Změna členských proměnných po vytvoření tohoto objektu COM nemá žádný vliv.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CConstantTransition`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller. h

##  <a name="cconstanttransition"></a>CConstantTransition::CConstantTransition

Vytvoří objekt přechodu a inicializuje jeho dobu trvání.

```
CConstantTransition (UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
Doba trvání přechodu.

##  <a name="create"></a>CConstantTransition:: Create

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

##  <a name="m_duration"></a>CConstantTransition::m_duration

Doba trvání přechodu.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
