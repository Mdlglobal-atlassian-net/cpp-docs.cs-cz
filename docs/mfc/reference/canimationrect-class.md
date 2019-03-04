---
title: Canimationrect – třída
ms.date: 11/04/2016
f1_keywords:
- CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationRect::GetBottom
- AFXANIMATIONCONTROLLER/CAnimationRect::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetLeft
- AFXANIMATIONCONTROLLER/CAnimationRect::GetRight
- AFXANIMATIONCONTROLLER/CAnimationRect::GetTop
- AFXANIMATIONCONTROLLER/CAnimationRect::GetValue
- AFXANIMATIONCONTROLLER/CAnimationRect::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bFixedSize
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bottomValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_leftValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_rightValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_szInitial
- AFXANIMATIONCONTROLLER/CAnimationRect::m_topValue
helpviewer_keywords:
- CAnimationRect [MFC], CAnimationRect
- CAnimationRect [MFC], AddTransition
- CAnimationRect [MFC], GetBottom
- CAnimationRect [MFC], GetDefaultValue
- CAnimationRect [MFC], GetLeft
- CAnimationRect [MFC], GetRight
- CAnimationRect [MFC], GetTop
- CAnimationRect [MFC], GetValue
- CAnimationRect [MFC], SetDefaultValue
- CAnimationRect [MFC], GetAnimationVariableList
- CAnimationRect [MFC], m_bFixedSize
- CAnimationRect [MFC], m_bottomValue
- CAnimationRect [MFC], m_leftValue
- CAnimationRect [MFC], m_rightValue
- CAnimationRect [MFC], m_szInitial
- CAnimationRect [MFC], m_topValue
ms.assetid: 0294156d-241e-4a57-92b2-31234fe557d6
ms.openlocfilehash: 84c4cf92894a9ece2021417445c9d7ab94ee6bdf
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259487"
---
# <a name="canimationrect-class"></a>Canimationrect – třída

Implementuje funkci obdélníku, jehož strany lze animovat.

## <a name="syntax"></a>Syntaxe

```
class CAnimationRect : public CAnimationBaseObject;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAnimationRect::CAnimationRect](#canimationrect)|Přetíženo. Vytvoří objekt rect animace.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationRect::AddTransition](#addtransition)|Přidá přechody pro levé straně, horní, pravé a dolní souřadnice.|
|[CAnimationRect::GetBottom](#getbottom)|Poskytuje přístup k canimationvariable – představuje dolní souřadnice.|
|[CAnimationRect::GetDefaultValue](#getdefaultvalue)|Vrátí výchozí hodnoty pro rozsah obdélníku.|
|[CAnimationRect::GetLeft](#getleft)|Poskytuje přístup k canimationvariable – představující Levá souřadnice.|
|[CAnimationRect::GetRight](#getright)|Poskytuje přístup k canimationvariable – představující Pravá souřadnice.|
|[CAnimationRect::GetTop](#gettop)|Poskytuje přístup k canimationvariable – představující horní souřadnici.|
|[CAnimationRect::GetValue](#getvalue)|Vrátí aktuální hodnotu.|
|[CAnimationRect::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnotu.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationRect::GetAnimationVariableList](#getanimationvariablelist)|Umístí animace zapouzdřené proměnné do seznamu. (Přepíše [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAnimationRect::operator RECT](#operator_rect)|Převede canimationrect – obdélníkový|
|[CAnimationRect::operator=](#operator_eq)|Rect – přiřadí canimationrect –.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CAnimationRect::m_bFixedSize](#m_bfixedsize)|Určuje, zda obdélník má pevnou velikost.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CAnimationRect::m_bottomValue](#m_bottomvalue)|Proměnné animace zapouzdřený objekt, který představuje dolní mez animace obdélníku.|
|[CAnimationRect::m_leftValue](#m_leftvalue)|Proměnné animace zapouzdřený objekt, který představuje vlevo mez animace obdélníku.|
|[CAnimationRect::m_rightValue](#m_rightvalue)|Proměnné animace zapouzdřený objekt, který představuje pravé mez animace obdélníku.|
|[CAnimationRect::m_szInitial](#m_szinitial)|Určuje počáteční velikost animace obdélníku.|
|[CAnimationRect::m_topValue](#m_topvalue)|Proměnné animace zapouzdřený objekt, který představuje horní mez animace obdélníku.|

## <a name="remarks"></a>Poznámky

Canimationrect – třída zapouzdří čtyři canimationvariable – objekty a může představovat v aplikacích obdélníku. Použít tuto třídu v aplikaci, stačí vytvořit instanci objektu této třídy, přidat řadič animace pomocí CAnimationController::AddAnimationObject a volání AddTransition pro každý přechod pro levé, pravé horní a dolní souřadnice.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationRect`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationRect::AddTransition

Přidá přechody pro levé straně, horní, pravé a dolní souřadnice.

```
void AddTransition(
    CBaseTransition* pLeftTransition,
    CBaseTransition* pTopTransition,
    CBaseTransition* pRightTransition,
    CBaseTransition* pBottomTransition);
```

### <a name="parameters"></a>Parametry

*pLeftTransition*<br/>
Určuje přechodu na levé straně.

*pTopTransition*<br/>
Určuje přechod pro horní strana.

*pRightTransition*<br/>
Určuje přechodu na pravé straně.

*pBottomTransition*<br/>
Určuje přechod pro dolní strana.

### <a name="remarks"></a>Poznámky

Voláním této funkce, které chcete přidat zadaného přechody do interní seznamu přechody má použít u proměnné animace pro jednotlivých stran obdélník. Při přidání přechody jsou nejsou okamžitě použity a uložené ve vnitřním seznamu. Jsou použity přechody (přidané do scénáře pro konkrétní hodnotu) při volání CAnimationController::AnimateGroup. Pokud není nutné použít s přechodem na jednu ze strany obdélník, můžete předat hodnotu NULL.

##  <a name="canimationrect"></a>  CAnimationRect::CAnimationRect

Vytvoří objekt canimationrect –.

```
CAnimationRect();

CAnimationRect(
    const CRect& rect,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);

CAnimationRect(
    const CPoint& pt,
    const CSize& sz,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);

CAnimationRect(
    int nLeft,
    int nTop,
    int nRight,
    int nBottom,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Určuje výchozí obdélník.

*nGroupID*<br/>
Určuje ID skupiny.

*nObjectID*<br/>
Určuje ID objektu.

*dwUserData*<br/>
Určuje data definovaná uživatelem.

*pt*<br/>
Souřadnice levého horního rohu.

*sz*<br/>
Velikost obdélník.

*nLeft*<br/>
Určuje souřadnice levého mez.

*nTop*<br/>
Určuje souřadnici horní vázána.

*nRight*<br/>
Určuje souřadnici pravého mez.

*nBottom*<br/>
Určuje souřadnici dolní vázána.

### <a name="remarks"></a>Poznámky

Objekt je vytvořen s výchozími hodnotami u vlevo, horní, pravé a dolního okraje, ID objektu a ID skupiny, který bude nastavený na hodnotu 0. Může se změnit později v době běhu pomocí SetDefaultValue a ID sady.

##  <a name="getanimationvariablelist"></a>  CAnimationRect::GetAnimationVariableList

Umístí animace zapouzdřené proměnné do seznamu.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*lst*<br/>
Pokud funkce vrátí, obsahuje odkazy na čtyři canimationvariable – objekty představující souřadnice obdélník.

##  <a name="getbottom"></a>  CAnimationRect::GetBottom

Poskytuje přístup k canimationvariable – představuje dolní souřadnice.

```
CAnimationVariable& GetBottom();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřený canimationvariable – představuje dolní souřadnice.

### <a name="remarks"></a>Poznámky

Můžete volat tuto metodu za účelem získání přímý přístup k podkladové canimationvariable – představuje dolní souřadnice.

##  <a name="getdefaultvalue"></a>  CAnimationRect::GetDefaultValue

Vrátí výchozí hodnoty pro rozsah obdélníku.

```
CRect GetDefaultValue();
```

### <a name="return-value"></a>Návratová hodnota

Crect – hodnotu obsahující výchozí hodnoty pro levé, pravé, horní a dolní.

### <a name="remarks"></a>Poznámky

Voláním této funkce načtete výchozí hodnotu, která byla dříve nastavil konstruktor nebo SetDefaultValue.

##  <a name="getleft"></a>  CAnimationRect::GetLeft

Poskytuje přístup k canimationvariable – představující Levá souřadnice.

```
CAnimationVariable& GetLeft();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřený canimationvariable – představující Levá souřadnice.

### <a name="remarks"></a>Poznámky

Můžete volat tuto metodu za účelem získání přímý přístup k podkladové canimationvariable – představující Levá souřadnice.

##  <a name="getright"></a>  CAnimationRect::GetRight

Poskytuje přístup k canimationvariable – představující Pravá souřadnice.

```
CAnimationVariable& GetRight();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřený canimationvariable – představující Pravá souřadnice.

### <a name="remarks"></a>Poznámky

Můžete volat tuto metodu za účelem získání přímý přístup k podkladové canimationvariable – představující Pravá souřadnice.

##  <a name="gettop"></a>  CAnimationRect::GetTop

Poskytuje přístup k canimationvariable – představující horní souřadnici.

```
CAnimationVariable& GetTop();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřený canimationvariable – představující horní souřadnici.

### <a name="remarks"></a>Poznámky

Můžete volat tuto metodu za účelem získání přímý přístup k podkladové canimationvariable – hlavní bod se souřadnicemi představující.

##  <a name="getvalue"></a>  CAnimationRect::GetValue

Vrátí aktuální hodnotu.

```
BOOL GetValue(CRect& rect);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Výstup. Po návratu metody obsahuje aktuální hodnotu.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud aktuální hodnota byla úspěšně získána; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Voláním této funkce k získání aktuální hodnoty animace obdélníku. Pokud tato metoda selže nebo základní COM objekty pro vlevo nahoře, vpravo a dole nejsou inicializované, rect obsahuje výchozí hodnotu, která byla dříve nastavena v konstruktoru nebo SetDefaultValue.

##  <a name="m_bfixedsize"></a>  CAnimationRect::m_bFixedSize

Určuje, zda obdélník má pevnou velikost.

```
BOOL m_bFixedSize;
```

### <a name="remarks"></a>Poznámky

Pokud je tento člen má hodnotu true, velikost obdélníku je pevná a doprava a hodnot dolní přepočítána pokaždé, když levém horním rohu se přesune podle pevné velikosti. Nastavte tuto hodnotu na TRUE, pokud chcete jednoduše přesunout obdélník kolem obrazovky. V tomto případě přechody použitý pro souřadnice vpravo a dole se ignorují. Velikost je při vytvoření objektu nebo volejte SetDefaultValue interně uložená. Ve výchozím nastavení je tento člen nastaven na hodnotu FALSE.

##  <a name="m_bottomvalue"></a>  CAnimationRect::m_bottomValue

Proměnné animace zapouzdřený objekt, který představuje dolní mez animace obdélníku.

```
CAnimationVariable m_bottomValue;
```

##  <a name="m_leftvalue"></a>  CAnimationRect::m_leftValue

Proměnné animace zapouzdřený objekt, který představuje vlevo mez animace obdélníku.

```
CAnimationVariable m_leftValue;
```

##  <a name="m_rightvalue"></a>  CAnimationRect::m_rightValue

Proměnné animace zapouzdřený objekt, který představuje pravé mez animace obdélníku.

```
CAnimationVariable m_rightValue;
```

##  <a name="m_szinitial"></a>  CAnimationRect::m_szInitial

Určuje počáteční velikost animace obdélníku.

```
CSize m_szInitial;
```

##  <a name="m_topvalue"></a>  CAnimationRect::m_topValue

Proměnné animace zapouzdřený objekt, který představuje horní mez animace obdélníku.

```
CAnimationVariable m_topValue;
```

##  <a name="operator_rect"></a>  CAnimationRect::operator RECT

Převede canimationrect – obdélníkový

```
operator RECT();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota animace obdélníku jako RECT.

### <a name="remarks"></a>Poznámky

Tato funkce volá interně GetValue. Pokud GetValue z nějakého důvodu selže, bude obsahovat vrácené RECT výchozí hodnoty pro všechny souřadnice obdélník.

##  <a name="operator_eq"></a>  CAnimationRect::operator =

Rect – přiřadí canimationrect –.

```
void operator=(const RECT& rect);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Nová hodnota animace obdélníku.

### <a name="remarks"></a>Poznámky

Doporučuje se provést před zahájením animace, vzhledem k tomu tento operátor volá SetDefaultValue, která znovu vytvoří objekty modelu COM pro barevné složky, pokud byl vytvořen. Pokud odebíráte tento objekt animace na události (ValueChanged nebo IntegerValueChanged), musíte znovu zapnout. Tyto události.

##  <a name="setdefaultvalue"></a>  CAnimationRect::SetDefaultValue

Nastaví výchozí hodnotu.

```
void SetDefaultValue(const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Určuje nové výchozí hodnoty pro vlevo, nahoře, vpravo a dole.

### <a name="remarks"></a>Poznámky

Tuto funkci použijte k nastavení výchozí hodnoty na objekt animace. Tyto metody přiřadí výchozí hodnoty hranice obdélníku. Také obnoví základní objekty modelu COM, pokud byl vytvořen. Pokud odebíráte tento objekt animace na události (ValueChanged nebo IntegerValueChanged), musíte znovu zapnout. Tyto události.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
