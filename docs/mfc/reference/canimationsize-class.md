---
title: CAnimationSize – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 80a90dfa37bc1d2c3c84e6451ae23af7ded767c2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369707"
---
# <a name="canimationsize-class"></a>CAnimationSize – třída

Implementuje funkce size objektu, jehož rozměry lze animovat.

## <a name="syntax"></a>Syntaxe

```
class CAnimationSize : public CAnimationBaseObject;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationSize::CAnimationSize](#canimationsize)|Přetíženo. Vytvoří objekt velikosti animace.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationSize::AddTransition](#addtransition)|Přidá přechody pro Šířka a Výška.|
|[CAnimationSize::GetCX](#getcx)|Poskytuje přístup k CAnimationVariable představující šířku.|
|[CAnimationSize::GetCY](#getcy)|Poskytuje přístup k CAnimationVariable představující Height.|
|[CAnimationSize::GetDefaultValue](#getdefaultvalue)|Vrátí výchozí hodnoty pro Šířka a Výška.|
|[CAnimationSize::GetValue](#getvalue)|Vrátí aktuální hodnotu.|
|[CAnimationSize::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnotu.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationSize::GetAnimationVariableList](#getanimationvariablelist)|Vloží zapouzdřené proměnné animace do seznamu. (Přepíše [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationSize::operátor CSize](#operator_csize)|Převede CAnimationSize csize CSize.|
|[CAnimationVelikost::operátor=](#operator_eq)|Přiřadí szSrc CAnimationSize.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationSize::m_cxValue](#m_cxvalue)|Zapouzdřená proměnná animace, která představuje šířku velikosti animace.|
|[CAnimationSize::m_cyValue](#m_cyvalue)|Zapouzdřená proměnná animace, která představuje výšku velikosti animace.|

## <a name="remarks"></a>Poznámky

Třída CAnimationSize zapouzdřuje dva objekty CAnimationVariable a může představovat v aplikacích velikost. Tuto třídu můžete například použít k animaci velikosti libovolného dvourozměrného objektu na obrazovce (například obdélník, ovládací prvek atd.). Chcete-li použít tuto třídu v aplikaci, stačí vytvořit instanci objektu této třídy, přidejte jej do ovladače animace pomocí CAnimationController::AddAnimationObject a volání AddTransition pro každý přechod, který má být použit na Šířku a/nebo Výška.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationSize`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="canimationsizeaddtransition"></a><a name="addtransition"></a>CAnimationSize::AddTransition

Přidá přechody pro Šířka a Výška.

```
void AddTransition(
    CBaseTransition* pCXTransition,
    CBaseTransition* pCYTransition);
```

### <a name="parameters"></a>Parametry

*pCXPřechod*<br/>
Ukazatel přechodu pro šířku.

*pCYPřechod*<br/>
Ukazatel přechodu pro Height.

### <a name="remarks"></a>Poznámky

Voláním této funkce přidáte zadané přechody do interního seznamu přechodů, které mají být použity pro proměnné animace pro Šířka a Výška. Když přidáte přechody, nejsou použity okamžitě a uloženy v interním seznamu. Přechody jsou použity (přidány do scénáře pro určitou hodnotu) při volání CAnimationController::AnimateGroup. Pokud nepotřebujete použít přechod na jednu z dimenzí, můžete předat hodnotu NULL.

## <a name="canimationsizecanimationsize"></a><a name="canimationsize"></a>CAnimationSize::CAnimationSize

Vytvoří objekt velikosti animace.

```
CAnimationSize();

CAnimationSize(
    const CSize& szDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*szVýchozí*<br/>
Určuje výchozí velikost.

*nID skupiny*<br/>
Určuje ID skupiny.

*nID objektu*<br/>
Určuje ID objektu.

*dwUserData*<br/>
Určuje uživatelem definovaná data.

### <a name="remarks"></a>Poznámky

Objekt je vytvořen s výchozími hodnotami šířky, výšky, ID objektu a ID skupiny, které budou nastaveny na hodnotu 0. Mohou být později změněny za běhu pomocí SetDefaultValue a SetID.

## <a name="canimationsizegetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationSize::GetAnimationVariableList

Vloží zapouzdřené proměnné animace do seznamu.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*Lst*<br/>
Když funkce vrátí, obsahuje ukazatele na dva CAnimationVariable objekty představující šířku a výšku.

## <a name="canimationsizegetcx"></a><a name="getcx"></a>CAnimationSize::GetCX

Poskytuje přístup k CAnimationVariable představující šířku.

```
CAnimationVariable& GetCX();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřené CAnimationVariable představující Šířka.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete volat získat přímý přístup k podkladové CAnimationVariable představující šířku.

## <a name="canimationsizegetcy"></a><a name="getcy"></a>CAnimationSize::GetCY

Poskytuje přístup k CAnimationVariable představující Height.

```
CAnimationVariable& GetCY();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na zapouzdřené CAnimationVariable představující Height.

### <a name="remarks"></a>Poznámky

Tuto metodu můžete volat získat přímý přístup k podkladové CAnimationVariable představující Height.

## <a name="canimationsizegetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationSize::GetDefaultValue

Vrátí výchozí hodnoty pro Šířka a Výška.

```
CSize GetDefaultValue();
```

### <a name="return-value"></a>Návratová hodnota

Objekt CSize obsahující výchozí hodnoty.

### <a name="remarks"></a>Poznámky

Voláním této funkce načtěte výchozí hodnotu, která byla dříve nastavena konstruktorem nebo hodnotou SetDefaultValue.

## <a name="canimationsizegetvalue"></a><a name="getvalue"></a>CAnimationSize::GetValue

Vrátí aktuální hodnotu.

```
BOOL GetValue(CSize& szValue);
```

### <a name="parameters"></a>Parametry

*szHodnota*<br/>
Výstup. Obsahuje aktuální hodnotu při této metodě vrátí.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla aktuální hodnota úspěšně načtena; jinak FALSE.

### <a name="remarks"></a>Poznámky

Volání této funkce načíst aktuální hodnotu velikosti animace. Pokud tato metoda selže nebo základní objekty COM pro šířku a velikost nebyly inicializovány, szValue obsahuje výchozí hodnotu, která byla dříve nastavena v konstruktoru nebo SetDefaultValue.

## <a name="canimationsizem_cxvalue"></a><a name="m_cxvalue"></a>CAnimationSize::m_cxValue

Zapouzdřená proměnná animace, která představuje šířku velikosti animace.

```
CAnimationVariable m_cxValue;
```

## <a name="canimationsizem_cyvalue"></a><a name="m_cyvalue"></a>CAnimationSize::m_cyValue

Zapouzdřená proměnná animace, která představuje výšku velikosti animace.

```
CAnimationVariable m_cyValue;
```

## <a name="canimationsizeoperator-csize"></a><a name="operator_csize"></a>CAnimationSize::operátor CSize

Převede CAnimationSize csize CSize.

```
operator CSize();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota velikosti animace jako CSize.

### <a name="remarks"></a>Poznámky

Tato funkce interně volá GetValue. Pokud GetValue z nějakého důvodu selže, vrácená velikost bude obsahovat výchozí hodnoty pro šířku a výšku.

## <a name="canimationsizeoperator"></a><a name="operator_eq"></a>CAnimationVelikost::operátor=

Přiřadí szSrc CAnimationSize.

```
void operator=(const CSize& szSrc);
```

### <a name="parameters"></a>Parametry

*szSrc*<br/>
Odkazuje na CSize nebo SIZE.

### <a name="remarks"></a>Poznámky

Přiřadí szSrc CAnimationSize. Doporučuje se to provést před zahájením animace, protože tento operátor volá SetDefaultValue, který znovu vytvoří základní objekty COM pro Šířka a Výška, pokud byly vytvořeny. Pokud jste se přihlásili k odběru tohoto objektu animace k událostem (ValueChanged nebo IntegerValueChanged), je třeba tyto události znovu povolit.

## <a name="canimationsizesetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationSize::SetDefaultValue

Nastaví výchozí hodnotu.

```
void SetDefaultValue(const CSize& szDefault);
```

### <a name="parameters"></a>Parametry

*szVýchozí*<br/>
Určuje novou výchozí velikost.

### <a name="remarks"></a>Poznámky

Pomocí této funkce můžete nastavit výchozí hodnotu na objekt animace. Tato metoda přiřadí výchozí hodnoty šířka a výška velikosti animace. Také znovu vytvoří základní objekty COM, pokud byly vytvořeny. Pokud jste se přihlásili k odběru tohoto objektu animace k událostem (ValueChanged nebo IntegerValueChanged), je třeba tyto události znovu povolit.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
