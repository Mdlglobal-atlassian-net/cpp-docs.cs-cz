---
title: Canimationvalue – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAnimationValue [MFC], CAnimationValue
- CAnimationValue [MFC], AddTransition
- CAnimationValue [MFC], GetValue
- CAnimationValue [MFC], GetVariable
- CAnimationValue [MFC], SetDefaultValue
- CAnimationValue [MFC], GetAnimationVariableList
- CAnimationValue [MFC], m_value
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 378af608ed9f7498b00563e841521b69a10e0b05
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418278"
---
# <a name="canimationvalue-class"></a>Canimationvalue – třída

Implementuje funkci objektu animace, který má jednu hodnotu.

## <a name="syntax"></a>Syntaxe

```
class CAnimationValue : public CAnimationBaseObject;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAnimationValue::CAnimationValue](#canimationvalue)|Přetíženo. Vytvoří objekt canimationvalue –.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationValue::AddTransition](#addtransition)|Přidá přechodu použít hodnotu.|
|[CAnimationValue::GetValue](#getvalue)|Přetíženo. Načte aktuální hodnotu.|
|[CAnimationValue::GetVariable](#getvariable)|Poskytuje přístup k zapouzdřenému animace proměnné.|
|[CAnimationValue::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnotu.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationValue::GetAnimationVariableList](#getanimationvariablelist)|Umístí animace zapouzdřené proměnné do seznamu. (Přepíše [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAnimationValue::operator DOUBLE](#operator_double)|Poskytuje převod mezi canimationvalue – a DOUBLE.|
|[CAnimationValue::operator INT32](#operator_int32)|Poskytuje převod mezi canimationvalue – a datový typ INT32.|
|[CAnimationValue::operator =](#operator_eq)|Přetíženo. Canimationvalue – přiřadí hodnotu typu INT32.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CAnimationValue::m_value](#m_value)|Zapouzdřený objekt animace proměnné, která představuje hodnotu animace.|

## <a name="remarks"></a>Poznámky

Canimationvalue – třída zapouzdří jeden objekt canimationvariable – a může představovat v aplikacích animovaný jednu hodnotu. Například můžete použít tuto třídu pro animovaný průhlednost (efekt slábnutí), úhel (Chcete-li otáčet objekty), nebo pro všechny ostatní případy, když budete chtít vytvořit animaci v závislosti na hodnotu single animovaný. Použít tuto třídu v aplikaci, stačí vytvořit instanci objektu této třídy, přidat řadič animace pomocí CAnimationController::AddAnimationObject a volat AddTransition pro každý přechod na použité pro hodnotu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Canimationbaseobject –](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationValue`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationValue::AddTransition

Přidá přechodu použít hodnotu.

```
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>Parametry

*pTransition*<br/>
Ukazatel na objekt přechodu.

### <a name="remarks"></a>Poznámky

Voláním této funkce přidat přechod na vnitřní seznam přechody použít proměnnou animace. Při přidání přechody jsou nejsou okamžitě použity a uložené ve vnitřním seznamu. Jsou použity přechody (přidané do scénáře pro konkrétní hodnotu) při volání CAnimationController::AnimateGroup.

##  <a name="canimationvalue"></a>  CAnimationValue::CAnimationValue

Vytvoří objekt canimationvalue –.

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

*nGroupID*<br/>
Určuje ID skupiny.

*nObjectID*<br/>
Určuje ID objektu.

*dwUserData*<br/>
Určuje data definovaná uživatelem.

### <a name="remarks"></a>Poznámky

Vytvoří objekt canimationvalue – s výchozí vlastností: výchozí hodnota, ID skupiny a ID objektu jsou nastaveny na hodnotu 0.

##  <a name="getanimationvariablelist"></a>  CAnimationValue::GetAnimationVariableList

Umístí animace zapouzdřené proměnné do seznamu.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*obrázků*<br/>
Po návratu funkce obsahuje ukazatel na canimationvariable – představující animovaný hodnotu.

##  <a name="getvalue"></a>  CAnimationValue::GetValue

Načte aktuální hodnotu.

```
BOOL GetValue(DOUBLE& dblValue);
BOOL GetValue(INT32& nValue);
```

### <a name="parameters"></a>Parametry

*dblValue*<br/>
Výstup. Po návratu funkce obsahuje aktuální hodnotu proměnné animace.

*nHodnota*<br/>
Výstup. Po návratu funkce obsahuje aktuální hodnotu proměnné animace.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud aktuální hodnota se načetla úspěšně; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Volání této funkce načtete aktuální hodnotu. Tato implementace volá zapouzdřený objekt modelu COM, a pokud volání selže, tato metoda vrátí výchozí hodnotu, která byla dříve nastavena v konstruktoru, nebo s SetDefaultValue.

##  <a name="getvariable"></a>  CAnimationValue::GetVariable

Poskytuje přístup k zapouzdřenému animace proměnné.

```
CAnimationVariable& GetVariable();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na proměnnou zapouzdřený animace.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pro přístup k proměnné zapouzdřený animace. Canimationvariable – získáte přístup k základní IUIAnimationVariable objekt, jehož ukazatel může mít hodnotu NULL, pokud nebyl vytvořen proměnné animace.

##  <a name="m_value"></a>  CAnimationValue::m_value

Zapouzdřený objekt animace proměnné, která představuje hodnotu animace.

```
CAnimationVariable m_value;
```

##  <a name="operator_double"></a>  CAnimationValue::operator DOUBLE

Poskytuje převod mezi canimationvalue – a DOUBLE.

```
operator DOUBLE();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota hodnota animace.

### <a name="remarks"></a>Poznámky

Poskytuje převod mezi canimationvalue – a DOUBLE. Interně tato metoda volá GetValue a neprovádí kontrolu chyb. Pokud GetValue selže, vrácená hodnota bude obsahovat výchozí hodnotu dříve nastavené v konstruktoru nebo s SetDefaultValue.

##  <a name="operator_int32"></a>  CAnimationValue::operator INT32

Poskytuje převod mezi canimationvalue – a datový typ INT32.

```
operator INT32();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota animace hodnotu jako celé číslo.

### <a name="remarks"></a>Poznámky

Poskytuje převod mezi canimationvalue – a datový typ INT32. Interně tato metoda volá GetValue a neprovádí kontrolu chyb. Pokud GetValue selže, vrácená hodnota bude obsahovat výchozí hodnotu dříve nastavené v konstruktoru nebo s SetDefaultValue.

##  <a name="operator_eq"></a>  CAnimationValue::operator =

Canimationvalue – přiřadí hodnotu DOUBLE.

```
void operator=(DOUBLE dblVal);
void operator=(INT32 nVal);
```

### <a name="parameters"></a>Parametry

*dblVal*<br/>
Určuje hodnotu pro přiřazení hodnoty animace.

*nVal*<br/>
Určuje hodnotu pro přiřazení hodnoty animace.

### <a name="remarks"></a>Poznámky

Canimationvalue – přiřadí hodnotu DOUBLE. Tato hodnota nastavena jako výchozí hodnotu pro proměnnou zapouzdřený animace. Pokud odebíráte tento objekt animace na události (ValueChanged nebo IntegerValueChanged), musíte znovu zapnout. Tyto události.

##  <a name="setdefaultvalue"></a>  CAnimationValue::SetDefaultValue

Nastaví výchozí hodnotu.

```
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>Parametry

*dblDefaultValue*<br/>
Určuje výchozí hodnotu.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k nastavení výchozí hodnoty. Výchozí hodnota se vrátí do aplikace při animaci nebyl spuštěn a/nebo základní objekt modelu COM není vytvořená. Pokud už je vytvořený na základní objekt modelu COM zapouzdřena v CAnimationVarible, znovu vytvoří tuto metodu, proto možná budete muset volat metody EnableValueChanged/EnableIntegerValueChanged znovu.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
