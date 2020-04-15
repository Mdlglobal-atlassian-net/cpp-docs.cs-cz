---
title: Třída ClinearTransitionFromSpeed
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
ms.openlocfilehash: 31c04c303e7e253ec4de41bf076130d19232aac0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372272"
---
# <a name="clineartransitionfromspeed-class"></a>Třída ClinearTransitionFromSpeed

Zapouzdřuje přechod lineární rychlosti.

## <a name="syntax"></a>Syntaxe

```
class CLinearTransitionFromSpeed : public CBaseTransition;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[ClinearTransitionFromSpeed::ClinearTransitionFromSpeed](#clineartransitionfromspeed)|Vytvoří objekt přechodu lineární rychlosti a inicializuje jej rychlostí a konečnou hodnotou.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[ClinearTransitionFromSpeed::Vytvořit](#create)|Volá knihovnu přechodu k vytvoření zapouzdřený přechod ový objekt COM. (Přepíše [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CLinearTransitionFromSpeed::m_dblFinalValue](#m_dblfinalvalue)|Hodnota proměnné animace na konci přechodu.|
|[CLinearTransitionFromSpeed::m_dblSpeed](#m_dblspeed)|Absolutní hodnota rychlosti proměnné.|

## <a name="remarks"></a>Poznámky

Během přechodu lineární rychlosti se hodnota proměnné animace změní zadanou rychlostí. Doba trvání přechodu je určena rozdílem mezi počáteční hodnotou a zadanou konečnou hodnotou. Vzhledem k tomu, že všechny přechody jsou vymazány automaticky, doporučuje se jim přidělit pomocí operátoru new. Zapouzdřený objekt IUIAnimationTransition COM je vytvořen CAnimationController::AnimateGroup, do té doby je null. Změna členských proměnných po vytvoření tohoto objektu COM nemá žádný vliv.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[ClinearTransitionFromSpeed](../../mfc/reference/clineartransitionfromspeed-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="clineartransitionfromspeedclineartransitionfromspeed"></a><a name="clineartransitionfromspeed"></a>ClinearTransitionFromSpeed::ClinearTransitionFromSpeed

Vytvoří objekt přechodu lineární rychlosti a inicializuje jej rychlostí a konečnou hodnotou.

```
CLinearTransitionFromSpeed(
    DOUBLE dblSpeed,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>Parametry

*rychlost dblSpeed*<br/>
Absolutní hodnota rychlosti proměnné.

*dblFinalValue*<br/>
Hodnota proměnné animace na konci přechodu.

## <a name="clineartransitionfromspeedcreate"></a><a name="create"></a>ClinearTransitionFromSpeed::Vytvořit

Volá knihovnu přechodu k vytvoření zapouzdřený přechod ový objekt COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parametry

*pKnihovna*<br/>
Ukazatel na [rozhraní IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), které definuje knihovnu standardních přechodů.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je přechod úspěšně vytvořen; jinak FALSE.

## <a name="clineartransitionfromspeedm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>CLinearTransitionFromSpeed::m_dblFinalValue

Hodnota proměnné animace na konci přechodu.

```
DOUBLE m_dblFinalValue;
```

## <a name="clineartransitionfromspeedm_dblspeed"></a><a name="m_dblspeed"></a>CLinearTransitionFromSpeed::m_dblSpeed

Absolutní hodnota rychlosti proměnné.

```
DOUBLE m_dblSpeed;
```

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
