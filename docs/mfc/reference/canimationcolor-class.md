---
title: Canimationcolor – třída
ms.date: 11/04/2016
f1_keywords:
- CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationColor::GetB
- AFXANIMATIONCONTROLLER/CAnimationColor::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetG
- AFXANIMATIONCONTROLLER/CAnimationColor::GetR
- AFXANIMATIONCONTROLLER/CAnimationColor::GetValue
- AFXANIMATIONCONTROLLER/CAnimationColor::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationColor::m_bValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_gValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_rValue
helpviewer_keywords:
- CAnimationColor [MFC], CAnimationColor
- CAnimationColor [MFC], AddTransition
- CAnimationColor [MFC], GetB
- CAnimationColor [MFC], GetDefaultValue
- CAnimationColor [MFC], GetG
- CAnimationColor [MFC], GetR
- CAnimationColor [MFC], GetValue
- CAnimationColor [MFC], SetDefaultValue
- CAnimationColor [MFC], GetAnimationVariableList
- CAnimationColor [MFC], m_bValue
- CAnimationColor [MFC], m_gValue
- CAnimationColor [MFC], m_rValue
ms.assetid: 88bfabd4-efeb-4652-87e8-304253d8e48c
ms.openlocfilehash: ee6003a22db78c2a510579c3d717fec887f8a6ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151172"
---
# <a name="canimationcolor-class"></a>Canimationcolor – třída

Implementuje funkce barev, jejichž komponenty červené, zelené a modré lze animovat.

## <a name="syntax"></a>Syntaxe

```
class CAnimationColor : public CAnimationBaseObject;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAnimationColor::CAnimationColor](#canimationcolor)|Přetíženo. Vytvoří objekt animace barev.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationColor::AddTransition](#addtransition)|Přidá přechody pro komponenty červené, zelené a modré.|
|[CAnimationColor::GetB](#getb)|Poskytuje přístup k canimationvariable – představující modré.|
|[CAnimationColor::GetDefaultValue](#getdefaultvalue)|Vrátí výchozí hodnoty pro součásti barvy.|
|[CAnimationColor::GetG](#getg)|Poskytuje přístup k canimationvariable – zelené představující.|
|[CAnimationColor::GetR](#getr)|Poskytuje přístup k canimationvariable – představující červené.|
|[CAnimationColor::GetValue](#getvalue)|Vrátí aktuální hodnotu.|
|[CAnimationColor::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnotu.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationColor::GetAnimationVariableList](#getanimationvariablelist)|Umístí animace zapouzdřené proměnné do seznamu. (Přepíše [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAnimationColor::operator COLORREF](#operator_colorref)||
|[CAnimationColor::operator =](#operator_eq)|Canimationcolor – přiřadí barvu.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CAnimationColor::m_bValue](#m_bvalue)|Proměnné animace zapouzdřený objekt, který reprezentuje hodnota modré animace barvy.|
|[CAnimationColor::m_gValue](#m_gvalue)|Proměnné animace zapouzdřený objekt, který reprezentuje hodnota zelené animace barvy.|
|[CAnimationColor::m_rValue](#m_rvalue)|Proměnné animace zapouzdřený objekt, který reprezentuje hodnota červené animace barvy.|

## <a name="remarks"></a>Poznámky

Canimationcolor – třída zapouzdří tři objekty canimationvariable – a může představovat v aplikacích barvu. Tuto třídu můžete použít například pro animaci barvy libovolného objektu na obrazovce (jako je barva textu, barva pozadí atd). Použít tuto třídu v aplikaci, stačí vytvořit instanci objektu této třídy, přidat řadič animace pomocí CAnimationController::AddAnimationObject a volat AddTransition pro každý přechod použít komponenty červené, zelené a modré.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationColor`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationColor::AddTransition

Přidá přechody pro komponenty červené, zelené a modré.

```
void AddTransition(
    CBaseTransition* pRTransition,
    CBaseTransition* pGTransition,
    CBaseTransition* pBTransition);
```

### <a name="parameters"></a>Parametry

*pRTransition*<br/>
Přechod pro červené.

*pGTransition*<br/>
Přechod pro zelené.

*pBTransition*<br/>
Přechod pro modré.

### <a name="remarks"></a>Poznámky

Voláním této funkce, které chcete přidat zadanou přechody do interní seznamu přechody má použít u proměnné animace představující barevným. Při přidání přechody jsou nejsou okamžitě použity a uložené ve vnitřním seznamu. Jsou použity přechody (přidané do scénáře pro konkrétní hodnotu) při volání CAnimationController::AnimateGroup. Pokud není nutné použít s přechodem na jednu z barevných složek, můžete předat hodnotu NULL.

##  <a name="canimationcolor"></a>  CAnimationColor::CAnimationColor

Vytvoří objekt canimationcolor –.

```
CAnimationColor();

CAnimationColor(
    COLORREF color,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*color*<br/>
Určuje výchozí barvu.

*nGroupID*<br/>
Určuje ID skupiny.

*nObjectID*<br/>
Určuje ID objektu.

*dwUserData*<br/>
Určuje data definovaná uživatelem.

### <a name="remarks"></a>Poznámky

Objekt je vytvořen s výchozími hodnotami u červená, zelená, modrá, ID objektu a ID skupiny, který bude nastavený na hodnotu 0. Může se změnit později v době běhu pomocí SetDefaultValue a ID sady.

##  <a name="getanimationvariablelist"></a>  CAnimationColor::GetAnimationVariableList

Umístí animace zapouzdřené proměnné do seznamu.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*lst*<br/>
Pokud funkce vrátí, obsahuje odkazy na tři objekty canimationvariable – které představují komponenty červené, zelené a modré.

##  <a name="getb"></a>  CAnimationColor::GetB

Poskytuje přístup k canimationvariable – představující modré.

```
CAnimationVariable& GetB();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřený canimationvariable – představující modré.

### <a name="remarks"></a>Poznámky

Můžete volat tuto metodu za účelem získání přímý přístup k podkladové canimationvariable – představující modré.

##  <a name="getdefaultvalue"></a>  CAnimationColor::GetDefaultValue

Vrátí výchozí hodnoty pro součásti barvy.

```
COLORREF GetDefaultValue();
```

### <a name="return-value"></a>Návratová hodnota

Hodnotu COLORREF obsahující výchozí hodnoty pro součásti RGB.

### <a name="remarks"></a>Poznámky

Voláním této funkce načtete výchozí hodnotu, která byla dříve nastavil konstruktor nebo SetDefaultValue.

##  <a name="getg"></a>  CAnimationColor::GetG

Poskytuje přístup k canimationvariable – zelené představující.

```
CAnimationVariable& GetG();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřený canimationvariable – představující zelené komponentu.

### <a name="remarks"></a>Poznámky

Můžete volat tuto metodu za účelem získání přímý přístup k podkladové canimationvariable – představující zelené.

##  <a name="getr"></a>  CAnimationColor::GetR

Poskytuje přístup k canimationvariable – představující červené.

```
CAnimationVariable& GetR();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřený canimationvariable – představující červené.

### <a name="remarks"></a>Poznámky

Můžete volat tuto metodu za účelem získání přímý přístup k podkladové canimationvariable – představující červené.

##  <a name="getvalue"></a>  CAnimationColor::GetValue

Vrátí aktuální hodnotu.

```
BOOL GetValue(COLORREF& color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
Výstup. Po návratu metody obsahuje aktuální hodnotu.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud aktuální hodnota byla úspěšně získána; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Voláním této funkce k získání aktuální hodnoty animace barvy. Pokud tato metoda selže nebo nejsou inicializované základní objekty modelu COM pro složky barvy, barvy obsahuje výchozí hodnotu, která byla dříve nastavena v konstruktoru nebo SetDefaultValue.

##  <a name="m_bvalue"></a>  CAnimationColor::m_bValue

Proměnné animace zapouzdřený objekt, který reprezentuje hodnota modré animace barvy.

```
CAnimationVariable m_bValue;
```

##  <a name="m_gvalue"></a>  CAnimationColor::m_gValue

Proměnné animace zapouzdřený objekt, který reprezentuje hodnota zelené animace barvy.

```
CAnimationVariable m_gValue;
```

##  <a name="m_rvalue"></a>  CAnimationColor::m_rValue

Proměnné animace zapouzdřený objekt, který reprezentuje hodnota červené animace barvy.

```
CAnimationVariable m_rValue;
```

##  <a name="operator_colorref"></a>  CAnimationColor::operator COLORREF

```
operator COLORREF();
```

### <a name="return-value"></a>Návratová hodnota

##  <a name="operator_eq"></a>  CAnimationColor::operator =

Canimationcolor – přiřadí barvu.

```
void operator=(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
Určuje nové hodnoty animace barev.

### <a name="remarks"></a>Poznámky

Doporučuje se provést před zahájením animace, vzhledem k tomu tento operátor volá SetDefaultValue, která znovu vytvoří objekty modelu COM pro barevné složky, pokud byl vytvořen. Pokud odebíráte tento objekt animace na události (ValueChanged nebo IntegerValueChanged), musíte znovu zapnout. Tyto události.

##  <a name="setdefaultvalue"></a>  CAnimationColor::SetDefaultValue

Nastaví výchozí hodnotu.

```
void SetDefaultValue(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
Určuje nové výchozí hodnoty pro součásti červené, zelené a modré.

### <a name="remarks"></a>Poznámky

Tuto funkci použijte k nastavení výchozí hodnoty na objekt animace. Tyto metody přiřadí výchozí hodnoty barevných složek animace barvy. Také obnoví základní objekty modelu COM, pokud byl vytvořen. Pokud odebíráte tento objekt animace na události (ValueChanged nebo IntegerValueChanged), musíte znovu zapnout. Tyto události.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
