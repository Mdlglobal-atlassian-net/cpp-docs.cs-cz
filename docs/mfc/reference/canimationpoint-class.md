---
title: Canimationpoint – třída
ms.date: 11/04/2016
f1_keywords:
- CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetX
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetY
- AFXANIMATIONCONTROLLER/CAnimationPoint::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_xValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_yValue
helpviewer_keywords:
- CAnimationPoint [MFC], CAnimationPoint
- CAnimationPoint [MFC], AddTransition
- CAnimationPoint [MFC], GetDefaultValue
- CAnimationPoint [MFC], GetValue
- CAnimationPoint [MFC], GetX
- CAnimationPoint [MFC], GetY
- CAnimationPoint [MFC], SetDefaultValue
- CAnimationPoint [MFC], GetAnimationVariableList
- CAnimationPoint [MFC], m_xValue
- CAnimationPoint [MFC], m_yValue
ms.assetid: 5dc4d46f-e695-4681-b15c-544b78b3e317
ms.openlocfilehash: 15f06d2fa3478570d2f784879a13e7b68515e746
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218535"
---
# <a name="canimationpoint-class"></a>Canimationpoint – třída

Implementuje funkci bodu, jehož souřadnice lze animovat.

## <a name="syntax"></a>Syntaxe

```
class CAnimationPoint : public CAnimationBaseObject;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAnimationPoint::CAnimationPoint](#canimationpoint)|Přetíženo. Vytvoří objekt canimationpoint –.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationPoint::AddTransition](#addtransition)|Přidá přechody pro X a Y.|
|[CAnimationPoint::GetDefaultValue](#getdefaultvalue)|Vrátí výchozí hodnoty pro X a Y.|
|[CAnimationPoint::GetValue](#getvalue)|Vrátí aktuální hodnotu.|
|[CAnimationPoint::GetX](#getx)|Poskytuje přístup k canimationvariable – pro souřadnici X.|
|[CAnimationPoint::GetY](#gety)|Poskytuje přístup k canimationvariable – souřadnici Y.|
|[CAnimationPoint::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnotu.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationPoint::GetAnimationVariableList](#getanimationvariablelist)|Umístí animace zapouzdřené proměnné do seznamu. (Přepíše [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAnimationPoint::operator CPoint](#operator_cpoint)|Převede canimationpoint – CPoint.|
|[CAnimationPoint::operator =](#operator_eq)|Přiřadí ptSrc canimationpoint –.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CAnimationPoint::m_xValue](#m_xvalue)|Proměnné animace zapouzdřený objekt, který představuje X souřadnice bodu animace.|
|[CAnimationPoint::m_yValue](#m_yvalue)|Proměnné animace zapouzdřený objekt, který představuje Souřadnice Y bodu animace.|

## <a name="remarks"></a>Poznámky

Canimationpoint – třída zapouzdří dva objekty canimationvariable – a může představovat v aplikacích bod. Například můžete použít tuto třídu pro animaci pozici objektu na obrazovce (například textový řetězec, kruh, bod atd). Použít tuto třídu v aplikaci, stačí vytvořit instanci objektu této třídy, přidáte jej do řadič animace pomocí CAnimationController::AddAnimationObject a volat AddTransition pro každý přechod použít souřadnice X a Y.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationPoint`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationPoint::AddTransition

Přidá přechody pro X a Y.

```
void AddTransition(
    CBaseTransition* pXTransition,
    CBaseTransition* pYTransition);
```

### <a name="parameters"></a>Parametry

*pXTransition*<br/>
Ukazatel na přechod pro souřadnice X.

*pYTransition*<br/>
Ukazatel na přechod pro vaši koordinaci.

### <a name="remarks"></a>Poznámky

Voláním této funkce, které chcete přidat zadaného přechody do interní seznamu přechody použít u proměnné animace pro X a Y. Při přidání přechody jsou nejsou okamžitě použity a uložené ve vnitřním seznamu. Jsou použity přechody (přidané do scénáře pro konkrétní hodnotu) při volání CAnimationController::AnimateGroup. Pokud není nutné použít s přechodem na jednu z souřadnice, lze předat hodnotu NULL.

##  <a name="canimationpoint"></a>  CAnimationPoint::CAnimationPoint

Vytvoří objekt canimationpoint –.

```
CAnimationPoint();

CAnimationPoint(
    const CPoint& ptDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*ptDefault*<br/>
Určuje souřadnice bodu výchozí.

*nGroupID*<br/>
Určuje ID skupiny.

*nObjectID*<br/>
Určuje ID objektu.

*dwUserData*<br/>
Určuje data definovaná uživatelem.

### <a name="remarks"></a>Poznámky

Vytvoří objekt canimationpoint – s výchozí vlastností: výchozí bod, ID skupiny a ID objektu jsou nastaveny na hodnotu 0.

##  <a name="getanimationvariablelist"></a>  CAnimationPoint::GetAnimationVariableList

Umístí animace zapouzdřené proměnné do seznamu.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*lst*<br/>
Pokud funkce vrátí, obsahuje odkazy na dva objekty canimationvariable – představující souřadnice X a Y.

##  <a name="getdefaultvalue"></a>  CAnimationPoint::GetDefaultValue

Vrátí výchozí hodnoty pro X a Y.

```
CPoint GetDefaultValue();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí hodnota obsahující bod.

### <a name="remarks"></a>Poznámky

Voláním této funkce načtete výchozí hodnotu, která byla dříve nastavil konstruktor nebo SetDefaultValue.

##  <a name="getvalue"></a>  CAnimationPoint::GetValue

Vrátí aktuální hodnotu.

```
BOOL GetValue(CPoint& ptValue);
```

### <a name="parameters"></a>Parametry

*ptValue*<br/>
Výstup. Po návratu metody obsahuje aktuální hodnotu.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud aktuální hodnota byla úspěšně získána; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Volání této funkce načtete aktuální hodnotu animace bodu. Pokud tato metoda selže nebo základní COM objekty x a Y souřadnice nejsou inicializované, ptValue obsahuje výchozí hodnotu, která byla dříve nastavena v konstruktoru nebo SetDefaultValue.

##  <a name="getx"></a>  CAnimationPoint::GetX

Poskytuje přístup k canimationvariable – pro souřadnici X.

```
CAnimationVariable& GetX();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřený canimationvariable – představující X koordinaci.

### <a name="remarks"></a>Poznámky

Můžete volat tuto metodu za účelem získání přímý přístup k podkladové canimationvariable – představující X koordinaci.

##  <a name="gety"></a>  CAnimationPoint::GetY

Poskytuje přístup k canimationvariable – souřadnici Y.

```
CAnimationVariable& GetY();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřený canimationvariable – představující souřadnici Y.

### <a name="remarks"></a>Poznámky

Můžete volat tuto metodu za účelem získání přímý přístup k podkladové canimationvariable – představující souřadnici Y.

##  <a name="m_xvalue"></a>  CAnimationPoint::m_xValue

Proměnné animace zapouzdřený objekt, který představuje X souřadnice bodu animace.

```
CAnimationVariable m_xValue;
```

##  <a name="m_yvalue"></a>  CAnimationPoint::m_yValue

Proměnné animace zapouzdřený objekt, který představuje Souřadnice Y bodu animace.

```
CAnimationVariable m_yValue;
```

##  <a name="operator_cpoint"></a>  CAnimationPoint::operator CPoint

Převede canimationpoint – CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota canimationpoint – jako CPoint.

### <a name="remarks"></a>Poznámky

Tato funkce volá interně GetValue. Pokud GetValue z nějakého důvodu selže, vrácená bodu bude obsahovat výchozí hodnoty pro X a Y.

##  <a name="operator_eq"></a>  CAnimationPoint::operator =

Přiřadí ptSrc canimationpoint –.

```
void operator=(const CPoint& ptSrc);
```

### <a name="parameters"></a>Parametry

*ptSrc*<br/>
Odkazuje na CPoint nebo bodu.

### <a name="remarks"></a>Poznámky

Přiřadí ptSrc canimationpoint –. Doporučuje se, že před jeho začátkem animace, vzhledem k tomu tento operátor volá SetDefaultValue, která znovu vytvoří základní COM objekty pro souřadnice X a Y Pokud byl vytvořen. Pokud odebíráte tento objekt animace na události (ValueChanged nebo IntegerValueChanged), musíte znovu zapnout. Tyto události.

##  <a name="setdefaultvalue"></a>  CAnimationPoint::SetDefaultValue

Nastaví výchozí hodnotu.

```
void SetDefaultValue(const POINT& ptDefault);
```

### <a name="parameters"></a>Parametry

*ptDefault*<br/>
Určuje výchozí hodnotu bodu.

### <a name="remarks"></a>Poznámky

Tuto funkci použijte k nastavení výchozí hodnoty na objekt animace. Této metody přiřadí výchozí hodnoty pro souřadnice X a Y bodu animace. Také obnoví základní objekty modelu COM, pokud byl vytvořen. Pokud odebíráte tento objekt animace na události (ValueChanged nebo IntegerValueChanged), musíte znovu zapnout. Tyto události.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
