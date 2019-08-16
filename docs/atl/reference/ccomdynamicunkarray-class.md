---
title: CComDynamicUnkArray – třída
ms.date: 11/04/2016
f1_keywords:
- CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::Add
- ATLCOM/ATL::CComDynamicUnkArray::begin
- ATLCOM/ATL::CComDynamicUnkArray::clear
- ATLCOM/ATL::CComDynamicUnkArray::end
- ATLCOM/ATL::CComDynamicUnkArray::GetAt
- ATLCOM/ATL::CComDynamicUnkArray::GetCookie
- ATLCOM/ATL::CComDynamicUnkArray::GetSize
- ATLCOM/ATL::CComDynamicUnkArray::GetUnknown
- ATLCOM/ATL::CComDynamicUnkArray::Remove
helpviewer_keywords:
- connection points [C++], managing
- CComDynamicUnkArray class
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
ms.openlocfilehash: d55a6d6bfbcc6921fa0633753365f5799388dc27
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497255"
---
# <a name="ccomdynamicunkarray-class"></a>CComDynamicUnkArray – třída

Tato třída ukládá pole `IUnknown` ukazatelů.

## <a name="syntax"></a>Syntaxe

```
class CComDynamicUnkArray
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|Konstruktor Inicializuje hodnoty kolekce na hodnotu NULL a velikost kolekce na hodnotu nula.|
|[CComDynamicUnkArray::~CComDynamicUnkArray](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComDynamicUnkArray:: Add](#add)|Voláním této metody přidáte `IUnknown` ukazatel do pole.|
|[CComDynamicUnkArray:: begin](#begin)|Vrátí ukazatel na první `IUnknown` ukazatel v kolekci.|
|[CComDynamicUnkArray:: Clear](#clear)|Vyprázdní pole.|
|[CComDynamicUnkArray:: end](#end)|Vrátí ukazatel na jeden za poslední `IUnknown` ukazatel v kolekci.|
|[CComDynamicUnkArray::GetAt](#getat)|Načte prvek na zadaném indexu.|
|[CComDynamicUnkArray:: GetCookie](#getcookie)|Voláním této metody získáte soubor cookie přidružený k danému `IUnknown` ukazateli.|
|[CComDynamicUnkArray:: GetSize](#getsize)|Vrátí délku pole.|
|[CComDynamicUnkArray:: getunknown](#getunknown)|Voláním této metody získáte `IUnknown` ukazatel přidružený k danému souboru cookie.|
|[CComDynamicUnkArray:: Remove](#remove)|Voláním této metody odeberete `IUnknown` ukazatel z pole.|

## <a name="remarks"></a>Poznámky

`CComDynamicUnkArray`obsahuje dynamicky přidělené pole `IUnknown` ukazatelů, každé rozhraní v bodu připojení. `CComDynamicUnkArray`dá se použít jako parametr pro třídu šablony [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .

Metody Begin a [End](#end) lze použít k procyklování všech bodů připojení (například při vyvolání události). [](#begin) `CComDynamicUnkArray`

Podrobnosti o automatizaci vytváření proxy bodů připojení najdete v tématu [přidání bodů připojení k objektu](../../atl/adding-connection-points-to-an-object.md) .

> [!NOTE]
> **Poznámka:** Třída `CComDynamicUnkArray` je používána průvodcem **přidáním třídy** při vytváření ovládacího prvku, který má spojovací body. Pokud chcete zadat počet přípojných bodů ručně `CComDynamicUnkArray` , změňte odkaz z na `>` `CComUnkArray<` n, kde *n* je počet požadovaných přípojných bodů.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="add"></a>CComDynamicUnkArray:: Add

Voláním této metody přidáte `IUnknown` ukazatel do pole.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
`IUnknown` Ukazatel, který se má přidat do pole

### <a name="return-value"></a>Návratová hodnota

Vrátí soubor cookie přidružený k nově přidanému ukazateli.

##  <a name="begin"></a>CComDynamicUnkArray:: begin

Vrátí ukazatel na začátek kolekce `IUnknown` ukazatelů rozhraní.

```
IUnknown**
    begin();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `IUnknown` ukazatel rozhraní.

### <a name="remarks"></a>Poznámky

Kolekce obsahuje ukazatele na rozhraní uložená místně jako `IUnknown`. Každé `IUnknown` rozhraní se přetypování na typ reálného rozhraní a pak se přes něj zavolá. Nejdřív není nutné zadávat dotazy na rozhraní.

Před použitím `IUnknown` rozhraní byste měli ověřit, že není null.

##  <a name="clear"></a>CComDynamicUnkArray:: Clear

Vyprázdní pole.

```
void clear();
```

##  <a name="ccomdynamicunkarray"></a>CComDynamicUnkArray::CComDynamicUnkArray

Konstruktor

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>Poznámky

Nastaví velikost kolekce na hodnotu nula a inicializuje hodnoty na hodnotu NULL. Destruktor uvolní kolekci, pokud je to nutné.

##  <a name="dtor"></a>CComDynamicUnkArray:: ~ CComDynamicUnkArray

Destruktor.

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>Poznámky

Uvolňuje prostředky přidělené konstruktorem třídy.

##  <a name="end"></a>CComDynamicUnkArray:: end

Vrátí ukazatel na jeden za poslední `IUnknown` ukazatel v kolekci.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `IUnknown` ukazatel rozhraní.

##  <a name="getat"></a>CComDynamicUnkArray::GetAt

Načte prvek na zadaném indexu.

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index elementu, který se má načíst

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) .

##  <a name="getcookie"></a>CComDynamicUnkArray:: GetCookie

Voláním této metody získáte soubor cookie přidružený k danému `IUnknown` ukazateli.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Parametry

*ppFind*<br/>
`IUnknown` Ukazatel, pro který je vyžadován přidružený soubor cookie.

### <a name="return-value"></a>Návratová hodnota

Vrátí soubor cookie přidružený `IUnknown` k ukazateli nebo nulu, pokud nebyl nalezen žádný odpovídající `IUnknown` ukazatel.

### <a name="remarks"></a>Poznámky

Pokud je k dispozici více než jedna instance stejného `IUnknown` ukazatele, vrátí tato funkce soubor cookie pro první z nich.

##  <a name="getsize"></a>CComDynamicUnkArray:: GetSize

Vrátí délku pole.

```
int GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka pole.

##  <a name="getunknown"></a>CComDynamicUnkArray:: getunknown

Voláním této metody získáte `IUnknown` ukazatel přidružený k danému souboru cookie.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie*<br/>
Soubor cookie, pro který je `IUnknown` vyžadován přidružený ukazatel.

### <a name="return-value"></a>Návratová hodnota

`IUnknown` Vrátí ukazatel nebo hodnotu null, pokud není nalezen žádný vyhovující soubor cookie.

##  <a name="remove"></a>CComDynamicUnkArray:: Remove

Voláním této metody odeberete `IUnknown` ukazatel z pole.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie*<br/>
Soubor cookie odkazující na `IUnknown` ukazatel, který má být odebrán z pole.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je ukazatel odstraněn. v opačném případě FALSE.

## <a name="see-also"></a>Viz také:

[CComUnkArray – třída](../../atl/reference/ccomunkarray-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
