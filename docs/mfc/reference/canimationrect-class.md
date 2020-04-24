---
title: CAnimationRect – třída
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
ms.openlocfilehash: 273ea2b548d35722ebf937d2db2b589fef5e69fa
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755132"
---
# <a name="canimationrect-class"></a>CAnimationRect – třída

Implementuje funkce obdélníku, jehož strany mohou být animovány.

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
|[CAnimationRect::AddTransition](#addtransition)|Přidá přechody pro souřadnice vlevo, nahoře, vpravo a dole.|
|[CAnimationRect::GetBottom](#getbottom)|Poskytuje přístup k CAnimationVariable představující dolní souřadnice.|
|[CAnimationRect::GetDefaultValue](#getdefaultvalue)|Vrátí výchozí hodnoty pro hranice obdélníku.|
|[CAnimationRect::GetLeft](#getleft)|Poskytuje přístup k CAnimationVariable představující levé souřadnice.|
|[CAnimationRect::GetRight](#getright)|Poskytuje přístup k CAnimationVariable představující pravé souřadnice.|
|[CAnimationRect::GetTop](#gettop)|Poskytuje přístup k CAnimationVariable představující nejvyšší souřadnice.|
|[CAnimationRect::Hodnota GetValue](#getvalue)|Vrátí aktuální hodnotu.|
|[CAnimationRect::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnotu.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationRect::GetAnimationVariableList](#getanimationvariablelist)|Vloží zapouzdřené proměnné animace do seznamu. (Přepíše [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAnimationRect::operátor RECT](#operator_rect)|Převede CAnimationRect na RECT.|
|[CAnimationRect::operátor=](#operator_eq)|Přiřadí rect CAnimationRect.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CAnimationRect::m_bFixedSize](#m_bfixedsize)|Určuje, zda má obdélník pevnou velikost.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Název|Popis|
|----------|-----------------|
|[CAnimationRect::m_bottomValue](#m_bottomvalue)|Zapouzdřená proměnná animace, která představuje dolní vazbu obdélníku animace.|
|[CAnimationRect::m_leftValue](#m_leftvalue)|Zapouzdřená proměnná animace, která představuje left bound animace obdélníku.|
|[CAnimationRect::m_rightValue](#m_rightvalue)|Zapouzdřená proměnná animace, která představuje pravovpravovousavý obdélník animace.|
|[CAnimationRect::m_szInitial](#m_szinitial)|Určuje počáteční velikost obdélníku animace.|
|[CAnimationRect::m_topValue](#m_topvalue)|Zapouzdřená proměnná animace, která představuje horní vazbu obdélníku animace.|

## <a name="remarks"></a>Poznámky

Třída CAnimationRect zapouzdřuje čtyři objekty CAnimationVariable a může v aplikacích představovat obdélník. Chcete-li použít tuto třídu v aplikaci, stačí vytvořit instanci objektu této třídy, přidejte jej do ovladače animace pomocí CAnimationController::AddAnimationObject a volání AddTransition pro každý přechod, který má být použit na levé, pravé horní a dolní souřadnice.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationRect`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="canimationrectaddtransition"></a><a name="addtransition"></a>CAnimationRect::AddTransition

Přidá přechody pro souřadnice vlevo, nahoře, vpravo a dole.

```cpp
void AddTransition(
    CBaseTransition* pLeftTransition,
    CBaseTransition* pTopTransition,
    CBaseTransition* pRightTransition,
    CBaseTransition* pBottomTransition);
```

### <a name="parameters"></a>Parametry

*pLeftTransition*<br/>
Určuje přechod pro levou stranu.

*pTopTransition*<br/>
Určuje přechod pro horní stranu.

*pRightTransition*<br/>
Určuje přechod pro pravou stranu.

*pBottomTransition*<br/>
Určuje přechod pro spodní stranu.

### <a name="remarks"></a>Poznámky

Volání této funkce přidat zadané přechody do vnitřního seznamu přechodů, které mají být použity pro proměnné animace pro každou stranu obdélníku. Když přidáte přechody, nejsou použity okamžitě a uloženy v interním seznamu. Přechody jsou použity (přidány do scénáře pro určitou hodnotu) při volání CAnimationController::AnimateGroup. Pokud nepotřebujete použít přechod na jednu ze stran obdélníku, můžete předat hodnotu NULL.

## <a name="canimationrectcanimationrect"></a><a name="canimationrect"></a>CAnimationRect::CAnimationRect

Vytvoří cAnimationRect objektu.

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

*nID skupiny*<br/>
Určuje ID skupiny.

*nID objektu*<br/>
Určuje ID objektu.

*dwUserData*<br/>
Určuje uživatelem definovaná data.

*Pt*<br/>
Souřadnice levého horního rohu.

*Sz*<br/>
Velikost obdélníku.

*nVlevo*<br/>
Určuje souřadnice levá vazba.

*nNahoře*<br/>
Určuje souřadnice horní hranice.

*nVpravo*<br/>
Určuje souřadnici vpravo vázané.

*nDolní část*<br/>
Určuje souřadnice dolní hranice.

### <a name="remarks"></a>Poznámky

Objekt je vytvořen s výchozími hodnotami pro levé, horní, pravé a dolní, ID objektu a ID skupiny, které budou nastaveny na 0. Mohou být později změněny za běhu pomocí SetDefaultValue a SetID.

## <a name="canimationrectgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationRect::GetAnimationVariableList

Vloží zapouzdřené proměnné animace do seznamu.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*Lst*<br/>
Když funkce vrátí, obsahuje ukazatele na čtyři CAnimationVariable objekty představující souřadnice obdélníku.

## <a name="canimationrectgetbottom"></a><a name="getbottom"></a>CAnimationRect::GetBottom

Poskytuje přístup k CAnimationVariable představující dolní souřadnice.

```
CAnimationVariable& GetBottom();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřené CAnimationVariable představující dolní souřadnice.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete volat, chcete-li získat přímý přístup k podkladové proměnné CAnimationVariable představující dolní souřadnice.

## <a name="canimationrectgetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationRect::GetDefaultValue

Vrátí výchozí hodnoty pro hranice obdélníku.

```
CRect GetDefaultValue();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota CRect obsahující výchozí hodnoty pro levé, pravé, horní a dolní.

### <a name="remarks"></a>Poznámky

Voláním této funkce načtěte výchozí hodnotu, která byla dříve nastavena konstruktorem nebo hodnotou SetDefaultValue.

## <a name="canimationrectgetleft"></a><a name="getleft"></a>CAnimationRect::GetLeft

Poskytuje přístup k CAnimationVariable představující levé souřadnice.

```
CAnimationVariable& GetLeft();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřené CAnimationVariable představující levé souřadnice.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete volat, chcete-li získat přímý přístup k podkladové proměnné CAnimationVariable představující levé souřadnice.

## <a name="canimationrectgetright"></a><a name="getright"></a>CAnimationRect::GetRight

Poskytuje přístup k CAnimationVariable představující pravé souřadnice.

```
CAnimationVariable& GetRight();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřené CAnimationVariable představující pravé souřadnice.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete volat získat přímý přístup k podkladové CAnimationVariable představující správné souřadnice.

## <a name="canimationrectgettop"></a><a name="gettop"></a>CAnimationRect::GetTop

Poskytuje přístup k CAnimationVariable představující nejvyšší souřadnice.

```
CAnimationVariable& GetTop();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřené CAnimationVariable představující nejvyšší souřadnice.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete volat získat přímý přístup k podkladové CAnimationVariable představující horní souřadnice.

## <a name="canimationrectgetvalue"></a><a name="getvalue"></a>CAnimationRect::Hodnota GetValue

Vrátí aktuální hodnotu.

```
BOOL GetValue(CRect& rect);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Výstup. Obsahuje aktuální hodnotu při této metodě vrátí.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla aktuální hodnota úspěšně načtena; jinak FALSE.

### <a name="remarks"></a>Poznámky

Volání této funkce načíst aktuální hodnotu obdélníkanimace. Pokud tato metoda selže nebo základní objekty COM pro levé, horní, pravé a dolní nebyly inicializovány, rect obsahuje výchozí hodnotu, která byla dříve nastavena v konstruktoru nebo SetDefaultValue.

## <a name="canimationrectm_bfixedsize"></a><a name="m_bfixedsize"></a>CAnimationRect::m_bFixedSize

Určuje, zda má obdélník pevnou velikost.

```
BOOL m_bFixedSize;
```

### <a name="remarks"></a>Poznámky

Pokud je tento člen true, pak je velikost obdélníku pevná a pravé a dolní hodnoty jsou přepočítány pokaždé, když je levý horní roh přesunut podle pevné velikosti. Nastavte tuto hodnotu na HODNOTU TRUE, abyste snadno přesunuli obdélník po obrazovce. V tomto případě jsou přechody aplikované na pravé a dolní souřadnice ignorovány. Velikost je uložena interně při vytváření objektu a/nebo volání SetDefaultValue. Ve výchozím nastavení je tento člen nastaven na hodnotu NEPRAVDA.

## <a name="canimationrectm_bottomvalue"></a><a name="m_bottomvalue"></a>CAnimationRect::m_bottomValue

Zapouzdřená proměnná animace, která představuje dolní vazbu obdélníku animace.

```
CAnimationVariable m_bottomValue;
```

## <a name="canimationrectm_leftvalue"></a><a name="m_leftvalue"></a>CAnimationRect::m_leftValue

Zapouzdřená proměnná animace, která představuje left bound animace obdélníku.

```
CAnimationVariable m_leftValue;
```

## <a name="canimationrectm_rightvalue"></a><a name="m_rightvalue"></a>CAnimationRect::m_rightValue

Zapouzdřená proměnná animace, která představuje pravovpravovousavý obdélník animace.

```
CAnimationVariable m_rightValue;
```

## <a name="canimationrectm_szinitial"></a><a name="m_szinitial"></a>CAnimationRect::m_szInitial

Určuje počáteční velikost obdélníku animace.

```
CSize m_szInitial;
```

## <a name="canimationrectm_topvalue"></a><a name="m_topvalue"></a>CAnimationRect::m_topValue

Zapouzdřená proměnná animace, která představuje horní vazbu obdélníku animace.

```
CAnimationVariable m_topValue;
```

## <a name="canimationrectoperator-rect"></a><a name="operator_rect"></a>CAnimationRect::operátor RECT

Převede CAnimationRect na RECT.

```
operator RECT();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota obdélníku animace jako RECT.

### <a name="remarks"></a>Poznámky

Tato funkce interně volá GetValue. Pokud GetValue z nějakého důvodu selže, vrácené RECT bude obsahovat výchozí hodnoty pro všechny souřadnice obdélníku.

## <a name="canimationrectoperator"></a><a name="operator_eq"></a>CAnimationRect::operátor=

Přiřadí rect CAnimationRect.

```cpp
void operator=(const RECT& rect);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Nová hodnota obdélníkanimace.

### <a name="remarks"></a>Poznámky

Doporučuje se to provést před zahájením animace, protože tento operátor volá SetDefaultValue, který znovu vytvoří základní objekty COM pro barevné komponenty, pokud byly vytvořeny. Pokud jste se přihlásili k odběru tohoto objektu animace k událostem (ValueChanged nebo IntegerValueChanged), je třeba tyto události znovu povolit.

## <a name="canimationrectsetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationRect::SetDefaultValue

Nastaví výchozí hodnotu.

```cpp
void SetDefaultValue(const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Určuje nové výchozí hodnoty pro levé, horní, pravé a dolní.

### <a name="remarks"></a>Poznámky

Pomocí této funkce můžete nastavit výchozí hodnotu na objekt animace. Tato metoda přiřadí výchozí hodnoty hranice obdélníku. Také znovu vytvoří základní objekty COM, pokud byly vytvořeny. Pokud jste se přihlásili k odběru tohoto objektu animace k událostem (ValueChanged nebo IntegerValueChanged), je třeba tyto události znovu povolit.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
