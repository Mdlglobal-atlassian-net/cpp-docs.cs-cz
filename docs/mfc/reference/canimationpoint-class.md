---
title: CAnimationPoint – třída
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
ms.openlocfilehash: 19f02010b6b73573a4800152e40c592fd1736ad5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369737"
---
# <a name="canimationpoint-class"></a>CAnimationPoint – třída

Implementuje funkce bodu, jehož souřadnice lze animovat.

## <a name="syntax"></a>Syntaxe

```
class CAnimationPoint : public CAnimationBaseObject;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationPoint::CAnimationPoint](#canimationpoint)|Přetíženo. Vytvoří cAnimationPoint objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationPoint::AddTransition](#addtransition)|Přidá přechody pro souřadnice X a Y.|
|[CAnimationPoint::GetDefaultValue](#getdefaultvalue)|Vrátí výchozí hodnoty pro souřadnice X a Y.|
|[CAnimationPoint::GetValue](#getvalue)|Vrátí aktuální hodnotu.|
|[CAnimationPoint::GetX](#getx)|Poskytuje přístup k CAnimationVariable pro souřadnice X.|
|[CanimationPoint::Gety](#gety)|Poskytuje přístup k CAnimationVariable pro souřadnice Y.|
|[CAnimationPoint::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnotu.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationPoint::GetAnimationVariableList](#getanimationvariablelist)|Vloží zapouzdřené proměnné animace do seznamu. (Přepíše [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationPoint::operátor CPoint](#operator_cpoint)|Převede CAnimationPoint na CPoint.|
|[CAnimationPoint::operátor=](#operator_eq)|Přiřadí ptSrc CAnimationPoint.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationPoint::m_xValue](#m_xvalue)|Zapouzdřená proměnná animace, která představuje souřadnici X bodu animace.|
|[CAnimationPoint::m_yValue](#m_yvalue)|Zapouzdřená proměnná animace, která představuje souřadnici Y bodu animace.|

## <a name="remarks"></a>Poznámky

Třída CAnimationPoint zapouzdřuje dva objekty CAnimationVariable a může v aplikacích představovat bod. Tuto třídu můžete například použít k animaci pozice libovolného objektu na obrazovce (například textového řetězce, kružnice, bodu atd.). Chcete-li použít tuto třídu v aplikaci, stačí vytvořit instanci objektu této třídy, přidejte jej do ovladače animace pomocí CAnimationController::AddAnimationObject a volání AddTransition pro každý přechod, který má být použit na souřadnice X nebo Y.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationPoint`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="canimationpointaddtransition"></a><a name="addtransition"></a>CAnimationPoint::AddTransition

Přidá přechody pro souřadnice X a Y.

```
void AddTransition(
    CBaseTransition* pXTransition,
    CBaseTransition* pYTransition);
```

### <a name="parameters"></a>Parametry

*pXPřechod*<br/>
Ukazatel přechodu pro souřadnice X.

*pYPřechod*<br/>
Ukazatel přechodu pro souřadnici Y.

### <a name="remarks"></a>Poznámky

Volánítéto funkce pro přidání zadaných přechodů do vnitřního seznamu přechodů, které mají být použity pro proměnné animace pro souřadnice X a Y. Když přidáte přechody, nejsou použity okamžitě a uloženy v interním seznamu. Přechody jsou použity (přidány do scénáře pro určitou hodnotu) při volání CAnimationController::AnimateGroup. Pokud nepotřebujete použít přechod na jednu z souřadnic, můžete předat hodnotu NULL.

## <a name="canimationpointcanimationpoint"></a><a name="canimationpoint"></a>CAnimationPoint::CAnimationPoint

Vytvoří cAnimationPoint objekt.

```
CAnimationPoint();

CAnimationPoint(
    const CPoint& ptDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*ptVýchozí*<br/>
Určuje souřadnice výchozího bodu.

*nID skupiny*<br/>
Určuje ID skupiny.

*nID objektu*<br/>
Určuje ID objektu.

*dwUserData*<br/>
Určuje uživatelem definovaná data.

### <a name="remarks"></a>Poznámky

Vytvoří objekt CAnimationPoint s výchozími vlastnostmi: souřadnice výchozího bodu, ID skupiny a ID objektu jsou nastaveny na 0.

## <a name="canimationpointgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationPoint::GetAnimationVariableList

Vloží zapouzdřené proměnné animace do seznamu.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*Lst*<br/>
Když funkce vrátí, obsahuje ukazatele na dva CAnimationVariable objekty představující Souřadnice X a Y.

## <a name="canimationpointgetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationPoint::GetDefaultValue

Vrátí výchozí hodnoty pro souřadnice X a Y.

```
CPoint GetDefaultValue();
```

### <a name="return-value"></a>Návratová hodnota

Bod obsahující výchozí hodnotu.

### <a name="remarks"></a>Poznámky

Voláním této funkce načtěte výchozí hodnotu, která byla dříve nastavena konstruktorem nebo hodnotou SetDefaultValue.

## <a name="canimationpointgetvalue"></a><a name="getvalue"></a>CAnimationPoint::GetValue

Vrátí aktuální hodnotu.

```
BOOL GetValue(CPoint& ptValue);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Výstup. Obsahuje aktuální hodnotu při této metodě vrátí.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla aktuální hodnota úspěšně načtena; jinak FALSE.

### <a name="remarks"></a>Poznámky

Volání této funkce načíst aktuální hodnotu bodu animace. Pokud tato metoda selže nebo základní objekty COM pro souřadnice X a Y nebyly inicializovány, hodnota ptValue obsahuje výchozí hodnotu, která byla dříve nastavena v konstruktoru nebo hodnotou SetDefaultValue.

## <a name="canimationpointgetx"></a><a name="getx"></a>CAnimationPoint::GetX

Poskytuje přístup k CAnimationVariable pro souřadnice X.

```
CAnimationVariable& GetX();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřené CAnimationVariable představující Souřadnice X.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete volat, chcete-li získat přímý přístup k podkladové proměnné CAnimationVariable představující souřadnice X.

## <a name="canimationpointgety"></a><a name="gety"></a>CanimationPoint::Gety

Poskytuje přístup k CAnimationVariable pro souřadnice Y.

```
CAnimationVariable& GetY();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřené CAnimationVariable představující Souřadnice Y.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete volat, chcete-li získat přímý přístup k podkladové proměnné CAnimationVariable představující souřadnice Y.

## <a name="canimationpointm_xvalue"></a><a name="m_xvalue"></a>CAnimationPoint::m_xValue

Zapouzdřená proměnná animace, která představuje souřadnici X bodu animace.

```
CAnimationVariable m_xValue;
```

## <a name="canimationpointm_yvalue"></a><a name="m_yvalue"></a>CAnimationPoint::m_yValue

Zapouzdřená proměnná animace, která představuje souřadnici Y bodu animace.

```
CAnimationVariable m_yValue;
```

## <a name="canimationpointoperator-cpoint"></a><a name="operator_cpoint"></a>CAnimationPoint::operátor CPoint

Převede CAnimationPoint na CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota CAnimationPoint jako CPoint.

### <a name="remarks"></a>Poznámky

Tato funkce interně volá GetValue. Pokud GetValue z nějakého důvodu selže, vrátí bod bude obsahovat výchozí hodnoty pro Souřadnice X a Y.

## <a name="canimationpointoperator"></a><a name="operator_eq"></a>CAnimationPoint::operátor=

Přiřadí ptSrc CAnimationPoint.

```
void operator=(const CPoint& ptSrc);
```

### <a name="parameters"></a>Parametry

*ptSrc*<br/>
Odkazuje na CPoint nebo POINT.

### <a name="remarks"></a>Poznámky

Přiřadí ptSrc CAnimationPoint. Doporučuje se to provést před zahájením animace, protože tento operátor volá SetDefaultValue, který znovu vytvoří základní objekty COM pro souřadnice X a Y, pokud byly vytvořeny. Pokud jste se přihlásili k odběru tohoto objektu animace k událostem (ValueChanged nebo IntegerValueChanged), je třeba tyto události znovu povolit.

## <a name="canimationpointsetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationPoint::SetDefaultValue

Nastaví výchozí hodnotu.

```
void SetDefaultValue(const POINT& ptDefault);
```

### <a name="parameters"></a>Parametry

*ptVýchozí*<br/>
Určuje výchozí bodovou hodnotu.

### <a name="remarks"></a>Poznámky

Pomocí této funkce můžete nastavit výchozí hodnotu na objekt animace. Tato metoda přiřadí výchozí hodnoty souřadnicím X a Y bodu animace. Také znovu vytvoří základní objekty COM, pokud byly vytvořeny. Pokud jste se přihlásili k odběru tohoto objektu animace k událostem (ValueChanged nebo IntegerValueChanged), je třeba tyto události znovu povolit.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
