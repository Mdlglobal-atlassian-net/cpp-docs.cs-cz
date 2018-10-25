---
title: Canimationsize – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCX
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCY
- AFXANIMATIONCONTROLLER/CAnimationSize::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetValue
- AFXANIMATIONCONTROLLER/CAnimationSize::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cxValue
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cyValue
dev_langs:
- C++
helpviewer_keywords:
- CAnimationSize [MFC], CAnimationSize
- CAnimationSize [MFC], AddTransition
- CAnimationSize [MFC], GetCX
- CAnimationSize [MFC], GetCY
- CAnimationSize [MFC], GetDefaultValue
- CAnimationSize [MFC], GetValue
- CAnimationSize [MFC], SetDefaultValue
- CAnimationSize [MFC], GetAnimationVariableList
- CAnimationSize [MFC], m_cxValue
- CAnimationSize [MFC], m_cyValue
ms.assetid: ea06d1b5-502c-44a3-82ca-8bd6ba6a9364
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c930c3e56d1b4c17ec2f9fdd1d81a98d6504b62
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065106"
---
# <a name="canimationsize-class"></a>Canimationsize – třída

Implementuje funkci objektu s rozměry, jehož rozměry lze animovat.

## <a name="syntax"></a>Syntaxe

```
class CAnimationSize : public CAnimationBaseObject;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAnimationSize::CAnimationSize](#canimationsize)|Přetíženo. Vytvoří objekt animace velikosti.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationSize::AddTransition](#addtransition)|Přidá přechody pro šířku a výšku.|
|[CAnimationSize::GetCX](#getcx)|Poskytuje přístup k canimationvariable – představující šířku.|
|[CAnimationSize::GetCY](#getcy)|Poskytuje přístup k canimationvariable – představující výšku.|
|[CAnimationSize::GetDefaultValue](#getdefaultvalue)|Vrátí výchozí hodnoty pro šířku a výšku.|
|[CAnimationSize::GetValue](#getvalue)|Vrátí aktuální hodnotu.|
|[CAnimationSize::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnotu.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationSize::GetAnimationVariableList](#getanimationvariablelist)|Umístí animace zapouzdřené proměnné do seznamu. (Přepíše [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAnimationSize::operator CSize](#operator_csize)|Převede canimationsize – CSize.|
|[CAnimationSize::operator =](#operator_eq)|Přiřadí szSrc canimationsize –.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CAnimationSize::m_cxValue](#m_cxvalue)|Proměnné animace zapouzdřený objekt, který představuje šířku velikosti animace.|
|[CAnimationSize::m_cyValue](#m_cyvalue)|Proměnné animace zapouzdřený objekt, který představuje výšku animace velikosti.|

## <a name="remarks"></a>Poznámky

Canimationsize – třída zapouzdří dva objekty canimationvariable – a může představovat v aplikacích s velikostí. Tuto třídu můžete použít například pro animaci velikost jakékoliv dva 3D objektu na obrazovce (například obdélníku, řídit atd). Použít tuto třídu v aplikaci, stačí vytvořit instanci objektu této třídy, přidat řadič animace pomocí CAnimationController::AddAnimationObject a volání AddTransition pro každý přechod uplatňovat na šířku nebo výšku.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Canimationbaseobject –](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationSize`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationSize::AddTransition

Přidá přechody pro šířku a výšku.

```
void AddTransition(
    CBaseTransition* pCXTransition,
    CBaseTransition* pCYTransition);
```

### <a name="parameters"></a>Parametry

*pCXTransition*<br/>
Ukazatel na přechod pro šířku.

*pCYTransition*<br/>
Ukazatel na přechod pro výšku.

### <a name="remarks"></a>Poznámky

Voláním této funkce, které chcete přidat zadanou přechody do interní seznamu přechody pro šířku a výšku použít pro proměnné animace. Při přidání přechody jsou nejsou okamžitě použity a uložené ve vnitřním seznamu. Jsou použity přechody (přidané do scénáře pro konkrétní hodnotu) při volání CAnimationController::AnimateGroup. Pokud není nutné použít s přechodem na jednu z dimenzí, můžete předat hodnotu NULL.

##  <a name="canimationsize"></a>  CAnimationSize::CAnimationSize

Vytvoří objekt animace velikosti.

```
CAnimationSize();

CAnimationSize(
    const CSize& szDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*szDefault*<br/>
Určuje výchozí velikost.

*nGroupID*<br/>
Určuje ID skupiny.

*nObjectID*<br/>
Určuje ID objektu.

*dwUserData*<br/>
Určuje data definovaná uživatelem.

### <a name="remarks"></a>Poznámky

Objekt je vytvořen s použitím výchozích hodnot pro šířku, výšku, objekt ID a ID skupiny, který bude nastavený na hodnotu 0. Může se změnit později v době běhu pomocí SetDefaultValue a ID sady.

##  <a name="getanimationvariablelist"></a>  CAnimationSize::GetAnimationVariableList

Umístí animace zapouzdřené proměnné do seznamu.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*obrázků*<br/>
Pokud funkce vrátí, obsahuje odkazy na dva objekty canimationvariable – reprezentující šířku a výšku.

##  <a name="getcx"></a>  CAnimationSize::GetCX

Poskytuje přístup k canimationvariable – představující šířku.

```
CAnimationVariable& GetCX();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřený canimationvariable – představující šířku.

### <a name="remarks"></a>Poznámky

Můžete volat tuto metodu za účelem získání přímý přístup k podkladové canimationvariable – představující šířku.

##  <a name="getcy"></a>  CAnimationSize::GetCY

Poskytuje přístup k canimationvariable – představující výšku.

```
CAnimationVariable& GetCY();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřený canimationvariable – představující výšku.

### <a name="remarks"></a>Poznámky

Můžete volat tuto metodu za účelem získání přímý přístup k podkladové canimationvariable – představující výšku.

##  <a name="getdefaultvalue"></a>  CAnimationSize::GetDefaultValue

Vrátí výchozí hodnoty pro šířku a výšku.

```
CSize GetDefaultValue();
```

### <a name="return-value"></a>Návratová hodnota

Objekt CSize obsahující výchozí hodnoty.

### <a name="remarks"></a>Poznámky

Voláním této funkce načtete výchozí hodnotu, která byla dříve nastavil konstruktor nebo SetDefaultValue.

##  <a name="getvalue"></a>  CAnimationSize::GetValue

Vrátí aktuální hodnotu.

```
BOOL GetValue(CSize& szValue);
```

### <a name="parameters"></a>Parametry

*szValue*<br/>
Výstup. Po návratu metody obsahuje aktuální hodnotu.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud aktuální hodnota byla úspěšně získána; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Volání této funkce načtete aktuální hodnotu velikosti animace. Pokud tato metoda selže nebo základní objekty modelu COM pro šířku a velikost nejsou inicializované, szValue obsahuje výchozí hodnotu, která byla dříve nastavena v konstruktoru nebo SetDefaultValue.

##  <a name="m_cxvalue"></a>  CAnimationSize::m_cxValue

Proměnné animace zapouzdřený objekt, který představuje šířku velikosti animace.

```
CAnimationVariable m_cxValue;
```

##  <a name="m_cyvalue"></a>  CAnimationSize::m_cyValue

Proměnné animace zapouzdřený objekt, který představuje výšku animace velikosti.

```
CAnimationVariable m_cyValue;
```

##  <a name="operator_csize"></a>  CAnimationSize::operator CSize

Převede canimationsize – CSize.

```
operator CSize();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota animace velikosti jako CSize.

### <a name="remarks"></a>Poznámky

Tato funkce volá interně GetValue. Pokud GetValue z nějakého důvodu selže, vrácená velikost bude obsahovat výchozí hodnoty pro šířku a výšku.

##  <a name="operator_eq"></a>  CAnimationSize::operator =

Přiřadí szSrc canimationsize –.

```
void operator=(const CSize& szSrc);
```

### <a name="parameters"></a>Parametry

*szSrc*<br/>
Odkazuje na CSize nebo velikosti.

### <a name="remarks"></a>Poznámky

Přiřadí szSrc canimationsize –. Doporučuje se provést před zahájením animace, vzhledem k tomu tento operátor volá SetDefaultValue, která znovu vytvoří objekty modelu COM pro šířku a výšku, pokud byl vytvořen. Pokud odebíráte tento objekt animace na události (ValueChanged nebo IntegerValueChanged), musíte znovu zapnout. Tyto události.

##  <a name="setdefaultvalue"></a>  CAnimationSize::SetDefaultValue

Nastaví výchozí hodnotu.

```
void SetDefaultValue(const CSize& szDefault);
```

### <a name="parameters"></a>Parametry

*szDefault*<br/>
Určuje novou velikost výchozí.

### <a name="remarks"></a>Poznámky

Tuto funkci použijte k nastavení výchozí hodnoty na objekt animace. Tyto metody přiřadí výchozí hodnoty pro šířku a výšku animace velikosti. Také obnoví základní objekty modelu COM, pokud byl vytvořen. Pokud odebíráte tento objekt animace na události (ValueChanged nebo IntegerValueChanged), musíte znovu zapnout. Tyto události.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
