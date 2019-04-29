---
title: Clineartransitionfromspeed – třída
ms.date: 11/04/2016
f1_keywords:
- CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::Create
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblSpeed
helpviewer_keywords:
- CLinearTransitionFromSpeed [MFC], CLinearTransitionFromSpeed
- CLinearTransitionFromSpeed [MFC], Create
- CLinearTransitionFromSpeed [MFC], m_dblFinalValue
- CLinearTransitionFromSpeed [MFC], m_dblSpeed
ms.assetid: 8f159a1c-8893-4017-951e-09e5758aba7d
ms.openlocfilehash: 1efa9806267958b4221ee112e56f242c7e25a8f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392502"
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

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CLinearTransitionFromSpeed](../../mfc/reference/clineartransitionfromspeed-class.md)

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

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
