---
title: Třída CAnimationColor
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
ms.openlocfilehash: 7c1c98d739aa1c17bb30df2d9d4ce8c41558c76d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750189"
---
# <a name="canimationcolor-class"></a>Třída CAnimationColor

Implementuje funkce barvy, jejíž červené, zelené a modré součásti lze animovat.

## <a name="syntax"></a>Syntaxe

```
class CAnimationColor : public CAnimationBaseObject;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CanimationColor::CanimationColor](#canimationcolor)|Přetíženo. Vytvoří objekt barvy animace.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationColor::AddTransition](#addtransition)|Přidá přechody pro komponenty červená, zelená a modrá.|
|[CAnimationColor::GetB](#getb)|Poskytuje přístup k CAnimationVariable představující blue komponentu.|
|[CanimationColor::GetDefaultValue](#getdefaultvalue)|Vrátí výchozí hodnoty pro barevné komponenty.|
|[CAnimationColor::GetG](#getg)|Poskytuje přístup k CAnimationVariable představující komponentu Green.|
|[CAnimationColor::Getr](#getr)|Poskytuje přístup k CAnimationVariable představující komponentu Red.|
|[CAnimationColor::Hodnota GetValue](#getvalue)|Vrátí aktuální hodnotu.|
|[CanimationColor::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnotu.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CanimationColor::GetAnimationVariableList](#getanimationvariablelist)|Vloží zapouzdřené proměnné animace do seznamu. (Přepíše [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAnimationColor::operátor COLORREF](#operator_colorref)||
|[CAnimationColor::operátor=](#operator_eq)|Přiřadí barvu CAnimationColor.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Název|Popis|
|----------|-----------------|
|[CAnimationColor::m_bValue](#m_bvalue)|Zapouzdřená proměnná animace, která představuje modrou složku barvy animace.|
|[CAnimationColor::m_gValue](#m_gvalue)|Zapouzdřená proměnná animace, která představuje zelenou složku barvy animace.|
|[CAnimationColor::m_rValue](#m_rvalue)|Zapouzdřená proměnná animace, která představuje červenou složku barvy animace.|

## <a name="remarks"></a>Poznámky

Třída CAnimationColor zapouzdřuje tři objekty CAnimationVariable a může v aplikacích představovat barvu. Tuto třídu můžete například použít k animaci barev libovolného objektu na obrazovce (například barvy textu, barvy pozadí atd.). Chcete-li použít tuto třídu v aplikaci, stačí vytvořit instanci objektu této třídy, přidejte jej do ovladače animace pomocí CAnimationController::AddAnimationObject a volání AddTransition pro každý přechod, který má být použit na komponenty red, green a blue.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationColor`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="canimationcoloraddtransition"></a><a name="addtransition"></a>CAnimationColor::AddTransition

Přidá přechody pro komponenty červená, zelená a modrá.

```cpp
void AddTransition(
    CBaseTransition* pRTransition,
    CBaseTransition* pGTransition,
    CBaseTransition* pBTransition);
```

### <a name="parameters"></a>Parametry

*pRPřechod*<br/>
Přechod pro komponentu Červená.

*pGPřechod*<br/>
Přechod pro komponentu Zelená.

*pBPřechod*<br/>
Přechod pro modrou komponentu.

### <a name="remarks"></a>Poznámky

Voláním této funkce přidáte zadané přechody do interního seznamu přechodů, které mají být použity na proměnné animace představující barevné komponenty. Když přidáte přechody, nejsou použity okamžitě a uloženy v interním seznamu. Přechody jsou použity (přidány do scénáře pro určitou hodnotu) při volání CAnimationController::AnimateGroup. Pokud nepotřebujete použít přechod na jednu z barevných složek, můžete předat hodnotu NULL.

## <a name="canimationcolorcanimationcolor"></a><a name="canimationcolor"></a>CanimationColor::CanimationColor

Vytvoří objekt CAnimationColor.

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

*nID skupiny*<br/>
Určuje ID skupiny.

*nID objektu*<br/>
Určuje ID objektu.

*dwUserData*<br/>
Určuje uživatelem definovaná data.

### <a name="remarks"></a>Poznámky

Objekt je vytvořen s výchozími hodnotami pro červenou, zelenou, modrou, ID objektu a ID skupiny, která bude nastavena na hodnotu 0. Mohou být později změněny za běhu pomocí SetDefaultValue a SetID.

## <a name="canimationcolorgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CanimationColor::GetAnimationVariableList

Vloží zapouzdřené proměnné animace do seznamu.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*Lst*<br/>
Když funkce vrátí, obsahuje ukazatele na tři CAnimationVariable objekty představující červené, zelené a modré komponenty.

## <a name="canimationcolorgetb"></a><a name="getb"></a>CAnimationColor::GetB

Poskytuje přístup k CAnimationVariable představující blue komponentu.

```
CAnimationVariable& GetB();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřené CAnimationVariable představující Blue komponenty.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete volat získat přímý přístup k podkladové CAnimationVariable představující Blue komponenty.

## <a name="canimationcolorgetdefaultvalue"></a><a name="getdefaultvalue"></a>CanimationColor::GetDefaultValue

Vrátí výchozí hodnoty pro barevné komponenty.

```
COLORREF GetDefaultValue();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota COLORREF obsahující výchozí hodnoty pro součásti RGB.

### <a name="remarks"></a>Poznámky

Voláním této funkce načtěte výchozí hodnotu, která byla dříve nastavena konstruktorem nebo hodnotou SetDefaultValue.

## <a name="canimationcolorgetg"></a><a name="getg"></a>CAnimationColor::GetG

Poskytuje přístup k CAnimationVariable představující komponentu Green.

```
CAnimationVariable& GetG();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřené CAnimationVariable představující zelené komponenty.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete volat získat přímý přístup k podkladové CAnimationVariable představující komponentu Green.

## <a name="canimationcolorgetr"></a><a name="getr"></a>CAnimationColor::Getr

Poskytuje přístup k CAnimationVariable představující komponentu Red.

```
CAnimationVariable& GetR();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřené CAnimationVariable představující komponentu Red.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete volat získat přímý přístup k podkladové CAnimationVariable představující komponentu Red.

## <a name="canimationcolorgetvalue"></a><a name="getvalue"></a>CAnimationColor::Hodnota GetValue

Vrátí aktuální hodnotu.

```
BOOL GetValue(COLORREF& color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
Výstup. Obsahuje aktuální hodnotu při této metodě vrátí.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla aktuální hodnota úspěšně načtena; jinak FALSE.

### <a name="remarks"></a>Poznámky

Volánítéto funkce načíst aktuální hodnotu barvy animace. Pokud tato metoda selže nebo základní objekty COM pro barevné komponenty nebyly inicializovány, barva obsahuje výchozí hodnotu, která byla dříve nastavena v konstruktoru nebo SetDefaultValue.

## <a name="canimationcolorm_bvalue"></a><a name="m_bvalue"></a>CAnimationColor::m_bValue

Zapouzdřená proměnná animace, která představuje modrou složku barvy animace.

```
CAnimationVariable m_bValue;
```

## <a name="canimationcolorm_gvalue"></a><a name="m_gvalue"></a>CAnimationColor::m_gValue

Zapouzdřená proměnná animace, která představuje zelenou složku barvy animace.

```
CAnimationVariable m_gValue;
```

## <a name="canimationcolorm_rvalue"></a><a name="m_rvalue"></a>CAnimationColor::m_rValue

Zapouzdřená proměnná animace, která představuje červenou složku barvy animace.

```
CAnimationVariable m_rValue;
```

## <a name="canimationcoloroperator-colorref"></a><a name="operator_colorref"></a>CAnimationColor::operátor COLORREF

```
operator COLORREF();
```

### <a name="return-value"></a>Návratová hodnota

## <a name="canimationcoloroperator"></a><a name="operator_eq"></a>CAnimationColor::operátor=

Přiřadí barvu CAnimationColor.

```cpp
void operator=(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
Určuje novou hodnotu Barva animace.

### <a name="remarks"></a>Poznámky

Doporučuje se to provést před zahájením animace, protože tento operátor volá SetDefaultValue, který znovu vytvoří základní objekty COM pro barevné komponenty, pokud byly vytvořeny. Pokud jste se přihlásili k odběru tohoto objektu animace k událostem (ValueChanged nebo IntegerValueChanged), je třeba tyto události znovu povolit.

## <a name="canimationcolorsetdefaultvalue"></a><a name="setdefaultvalue"></a>CanimationColor::SetDefaultValue

Nastaví výchozí hodnotu.

```cpp
void SetDefaultValue(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
Určuje nové výchozí hodnoty pro červené, zelené a modré součásti.

### <a name="remarks"></a>Poznámky

Pomocí této funkce můžete nastavit výchozí hodnotu na objekt animace. Tato metoda přiřadí výchozí hodnoty barevným složkám barvy animace. Také znovu vytvoří základní objekty COM, pokud byly vytvořeny. Pokud jste se přihlásili k odběru tohoto objektu animace k událostem (ValueChanged nebo IntegerValueChanged), je třeba tyto události znovu povolit.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
