---
title: Clineartransitionfromspeed – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::Create
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblSpeed
dev_langs:
- C++
helpviewer_keywords:
- CLinearTransitionFromSpeed [MFC], CLinearTransitionFromSpeed
- CLinearTransitionFromSpeed [MFC], Create
- CLinearTransitionFromSpeed [MFC], m_dblFinalValue
- CLinearTransitionFromSpeed [MFC], m_dblSpeed
ms.assetid: 8f159a1c-8893-4017-951e-09e5758aba7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54207bdd792d5ef6dc56630d52e699a0599f5d98
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446189"
---
# <a name="clineartransitionfromspeed-class"></a>Clineartransitionfromspeed – třída

Zapouzdřuje přechod lineární rychlostí.

## <a name="syntax"></a>Syntaxe

```
class CLinearTransitionFromSpeed : public CBaseTransition;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CLinearTransitionFromSpeed::CLinearTransitionFromSpeed](#clineartransitionfromspeed)|Vytvoří objekt přechod s lineární rychlostí a inicializuje ji s rychlostí a konečná hodnota.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CLinearTransitionFromSpeed::Create](#create)|Knihovna přechod k vytvoření objektu přechod zapouzdřený objekt modelu COM zavolá. (Přepíše [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CLinearTransitionFromSpeed::m_dblFinalValue](#m_dblfinalvalue)|Hodnota proměnné animace na konci přechodu.|
|[CLinearTransitionFromSpeed::m_dblSpeed](#m_dblspeed)|Absolutní hodnota proměnné rychlosti.|

## <a name="remarks"></a>Poznámky

Během přechodu lineární rychlostí hodnota proměnné animace změní na určenou míru. Dobu trvání přechodu určuje rozdíl mezi počáteční hodnotou a zadané konečnou hodnotu. Protože všechny přechody jsou automaticky vymazány, doporučuje se je přidělena pomocí operátoru nové. Zapouzdřený objekt IUIAnimationTransition COM je vytvořené CAnimationController::AnimateGroup, dokud je NULL. Změna členské proměnné po vytvoření tohoto objektu COM nemá žádný vliv.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cbasetransition –](../../mfc/reference/cbasetransition-class.md)

[Clineartransitionfromspeed –](../../mfc/reference/clineartransitionfromspeed-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="clineartransitionfromspeed"></a>  CLinearTransitionFromSpeed::CLinearTransitionFromSpeed

Vytvoří objekt přechod s lineární rychlostí a inicializuje ji s rychlostí a konečná hodnota.

```
CLinearTransitionFromSpeed(
    DOUBLE dblSpeed,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>Parametry

*dblSpeed*<br/>
Absolutní hodnota proměnné rychlosti.

*dblFinalValue*<br/>
Hodnota proměnné animace na konci přechodu.

##  <a name="create"></a>  CLinearTransitionFromSpeed::Create

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

##  <a name="m_dblfinalvalue"></a>  CLinearTransitionFromSpeed::m_dblFinalValue

Hodnota proměnné animace na konci přechodu.

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_dblspeed"></a>  CLinearTransitionFromSpeed::m_dblSpeed

Absolutní hodnota proměnné rychlosti.

```
DOUBLE m_dblSpeed;
```

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
