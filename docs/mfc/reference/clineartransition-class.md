---
title: Clineartransition – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::Create
- AFXANIMATIONCONTROLLER/CLinearTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransition::m_duration
dev_langs:
- C++
helpviewer_keywords:
- CLinearTransition [MFC], CLinearTransition
- CLinearTransition [MFC], Create
- CLinearTransition [MFC], m_dblFinalValue
- CLinearTransition [MFC], m_duration
ms.assetid: 7fcb2dba-beb8-4933-9f5d-3b7fb1585ef0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0eb283b40c860df148cb9c193f7b00a05ecb78c6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395606"
---
# <a name="clineartransition-class"></a>Clineartransition – třída

Zapouzdřuje lineární přechod.

## <a name="syntax"></a>Syntaxe

```
class CLinearTransition : public CBaseTransition;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CLinearTransition::CLinearTransition](#clineartransition)|Vytvoří objekt lineární přechod a inicializuje ji s doba trvání a konečná hodnota.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CLinearTransition::Create](#create)|Knihovna přechod k vytvoření objektu přechod zapouzdřený objekt modelu COM zavolá. (Přepíše [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CLinearTransition::m_dblFinalValue](#m_dblfinalvalue)|Hodnota proměnné animace na konci přechodu.|
|[CLinearTransition::m_duration](#m_duration)|Doba trvání přechodu.|

## <a name="remarks"></a>Poznámky

Během lineárního přechodu je hodnotu proměnné animace přechází lineárně od počáteční hodnoty do zadaného konečnou hodnotu. Protože všechny přechody jsou automaticky vymazány, doporučuje se je přidělena pomocí operátoru nové. Zapouzdřený objekt IUIAnimationTransition COM je vytvořené CAnimationController::AnimateGroup, dokud je NULL. Změna členské proměnné po vytvoření tohoto objektu COM nemá žádný vliv.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cbasetransition –](../../mfc/reference/cbasetransition-class.md)

[Clineartransition –](../../mfc/reference/clineartransition-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="clineartransition"></a>  CLinearTransition::CLinearTransition

Vytvoří objekt lineární přechod a inicializuje ji s doba trvání a konečná hodnota.

```
CLinearTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
Doba trvání přechodu.

*dblFinalValue*<br/>
Hodnota proměnné animace na konci přechodu.

##  <a name="create"></a>  CLinearTransition::Create

Knihovna přechod k vytvoření objektu přechod zapouzdřený objekt modelu COM zavolá.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parametry

*pLibrary*<br/>
Ukazatel na [IUIAnimationTransitionLibrary rozhraní](/windows/desktop/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), která definuje knihovnu standardní přechodů.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud úspěšně; vytvoření přechodu v opačném případě FALSE.

##  <a name="m_dblfinalvalue"></a>  CLinearTransition::m_dblFinalValue

Hodnota proměnné animace na konci přechodu.

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_duration"></a>  CLinearTransition::m_duration

Doba trvání přechodu.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
