---
title: Třída CAnimationValue
ms.date: 11/04/2016
f1_keywords:
- CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationValue::GetValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationValue::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationValue::m_value
helpviewer_keywords:
- CAnimationValue [MFC], CAnimationValue
- CAnimationValue [MFC], AddTransition
- CAnimationValue [MFC], GetValue
- CAnimationValue [MFC], GetVariable
- CAnimationValue [MFC], SetDefaultValue
- CAnimationValue [MFC], GetAnimationVariableList
- CAnimationValue [MFC], m_value
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
ms.openlocfilehash: 0437f0fc66f64ccb99157330154bf5aa4b5666b3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321975"
---
# <a name="canimationvalue-class"></a>Třída CAnimationValue

Implementuje funkce objektu animace, který má jednu hodnotu.

## <a name="syntax"></a>Syntaxe

```
class CAnimationValue : public CAnimationBaseObject;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationValue::CAnimationValue](#canimationvalue)|Přetíženo. Vytvoří objekt CAnimationValue.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationValue::AddTransition](#addtransition)|Přidá přechod, který má být použit na hodnotu.|
|[CAnimationValue::Hodnota GetValue](#getvalue)|Přetíženo. Načte aktuální hodnotu.|
|[CAnimationValue::Proměnná](#getvariable)|Poskytuje přístup k zapouzdřené proměnné animace.|
|[CAnimationValue::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnotu.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationValue::GetAnimationVariableList](#getanimationvariablelist)|Vloží zapouzdřenou proměnnou animace do seznamu. (Přepíše [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationValue::operátor DOUBLE](#operator_double)|Poskytuje převod mezi CAnimationValue a DOUBLE.|
|[CAnimationValue::operátor INT32](#operator_int32)|Poskytuje převod mezi CAnimationValue a INT32.|
|[CAnimationValue::operátor=](#operator_eq)|Přetíženo. Přiřadí hodnotu INT32 hodnotě CAnimationValue.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationValue::m_value](#m_value)|Zapouzdřená proměnná animace, která představuje hodnotu animace.|

## <a name="remarks"></a>Poznámky

Třída CAnimationValue zapouzdřuje jeden objekt CAnimationVariable a může v aplikacích představovat jednu animovanou hodnotu. Tuto třídu můžete například použít pro animovanou průhlednost (efekt zeslabení), úhel (k otočení objektů) nebo pro jakýkoli jiný případ, kdy potřebujete vytvořit animaci v závislosti na jedné animované hodnotě. Chcete-li použít tuto třídu v aplikaci, stačí vytvořit instanci objektu této třídy, přidejte jej do ovladače animace pomocí CAnimationController::AddAnimationObject a volání AddTransition pro každý přechod, který má být použit na hodnotu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationValue`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="canimationvalueaddtransition"></a><a name="addtransition"></a>CAnimationValue::AddTransition

Přidá přechod, který má být použit na hodnotu.

```
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>Parametry

*pPřechod*<br/>
Ukazatel na objekt přechodu.

### <a name="remarks"></a>Poznámky

Volánítéto funkce chcete přidat přechod do vnitřního seznamu přechodů, které mají být použity na proměnnou animace. Když přidáte přechody, nejsou použity okamžitě a uloženy v interním seznamu. Přechody jsou použity (přidány do scénáře pro určitou hodnotu) při volání CAnimationController::AnimateGroup.

## <a name="canimationvaluecanimationvalue"></a><a name="canimationvalue"></a>CAnimationValue::CAnimationValue

Vytvoří objekt CAnimationValue.

```
CAnimationValue();

CAnimationValue(
    DOUBLE dblDefaultValue,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*dblDefaultValue*<br/>
Určuje výchozí hodnotu.

*nID skupiny*<br/>
Určuje ID skupiny.

*nID objektu*<br/>
Určuje ID objektu.

*dwUserData*<br/>
určuje uživatelem definovaná data.

### <a name="remarks"></a>Poznámky

Konstrukce objektu CAnimationValue s výchozími vlastnostmi: výchozí hodnota, ID skupiny a ID objektu jsou nastaveny na 0.

## <a name="canimationvaluegetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationValue::GetAnimationVariableList

Vloží zapouzdřenou proměnnou animace do seznamu.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*Lst*<br/>
Když funkce vrátí, obsahuje ukazatel CAnimationVariable představující animovanou hodnotu.

## <a name="canimationvaluegetvalue"></a><a name="getvalue"></a>CAnimationValue::Hodnota GetValue

Načte aktuální hodnotu.

```
BOOL GetValue(DOUBLE& dblValue);
BOOL GetValue(INT32& nValue);
```

### <a name="parameters"></a>Parametry

*hodnota dblValue*<br/>
Výstup. Když funkce vrátí, obsahuje aktuální hodnotu proměnné animace.

*nHodnota*<br/>
Výstup. Když funkce vrátí, obsahuje aktuální hodnotu proměnné animace.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla aktuální hodnota úspěšně načtena; jinak FALSE.

### <a name="remarks"></a>Poznámky

Volání této funkce načíst aktuální hodnotu. Tato implementace volá zapouzdřený objekt COM a pokud volání selže, tato metoda vrátí výchozí hodnotu, která byla dříve nastavena v konstruktoru nebo s SetDefaultValue.

## <a name="canimationvaluegetvariable"></a><a name="getvariable"></a>CAnimationValue::Proměnná

Poskytuje přístup k zapouzdřené proměnné animace.

```
CAnimationVariable& GetVariable();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřenou proměnnou animace.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pro přístup k zapouzdřené proměnné animace. Z CAnimationVariable získáte přístup k podkladovému objektu IUIAnimationVariable, jehož ukazatel může být NULL, pokud nebyla vytvořena proměnná animace.

## <a name="canimationvaluem_value"></a><a name="m_value"></a>CAnimationValue::m_value

Zapouzdřená proměnná animace, která představuje hodnotu animace.

```
CAnimationVariable m_value;
```

## <a name="canimationvalueoperator-double"></a><a name="operator_double"></a>CAnimationValue::operátor DOUBLE

Poskytuje převod mezi CAnimationValue a DOUBLE.

```
operator DOUBLE();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota hodnoty animace.

### <a name="remarks"></a>Poznámky

Poskytuje převod mezi CAnimationValue a DOUBLE. Tato metoda interně volá GetValue a nekontroluje chyby. Pokud hodnota GetValue selže, vrácená hodnota bude obsahovat výchozí hodnotu, která byla dříve nastavena v konstruktoru nebo s hodnotou SetDefaultValue.

## <a name="canimationvalueoperator-int32"></a><a name="operator_int32"></a>CAnimationValue::operátor INT32

Poskytuje převod mezi CAnimationValue a INT32.

```
operator INT32();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota hodnoty animace jako celé číslo.

### <a name="remarks"></a>Poznámky

Poskytuje převod mezi CAnimationValue a INT32. Tato metoda interně volá GetValue a nekontroluje chyby. Pokud hodnota GetValue selže, vrácená hodnota bude obsahovat výchozí hodnotu, která byla dříve nastavena v konstruktoru nebo s hodnotou SetDefaultValue.

## <a name="canimationvalueoperator"></a><a name="operator_eq"></a>CAnimationValue::operátor=

Přiřadí hodnotu DOUBLE hodnotě CAnimationValue.

```
void operator=(DOUBLE dblVal);
void operator=(INT32 nVal);
```

### <a name="parameters"></a>Parametry

*dblVal*<br/>
Určuje hodnotu, která má být přiřazena hodnotě animace.

*nVal*<br/>
Určuje hodnotu, která má být přiřazena hodnotě animace.

### <a name="remarks"></a>Poznámky

Přiřadí hodnotu DOUBLE hodnotě CAnimationValue. Tato hodnota je nastavena jako výchozí hodnota pro zapouzdřenou proměnnou animace. Pokud jste se přihlásili k odběru tohoto objektu animace k událostem (ValueChanged nebo IntegerValueChanged), je třeba tyto události znovu povolit.

## <a name="canimationvaluesetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationValue::SetDefaultValue

Nastaví výchozí hodnotu.

```
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>Parametry

*dblDefaultValue*<br/>
Určuje výchozí hodnotu.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete nastavit výchozí hodnotu. Výchozí hodnota je vrácena do aplikace, pokud animace nebyla spuštěna a/nebo základní objekt COM nebyl vytvořen. Pokud základní objekt COM zapouzdřený v CAnimationVarible byl již vytvořen, tato metoda jej znovu vytvoří, proto možná budete muset znovu volat metody EnableValueChanged/EnableIntegerValueChanged.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
