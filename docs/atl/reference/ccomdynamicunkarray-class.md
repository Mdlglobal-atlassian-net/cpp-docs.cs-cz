---
title: Třída CComDynamicUnkArray
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
ms.openlocfilehash: 51b1d7e81c98bd5dbcf957b1705e7a717bfb9ab0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747988"
---
# <a name="ccomdynamicunkarray-class"></a>Třída CComDynamicUnkArray

Tato třída ukládá `IUnknown` pole ukazatelů.

## <a name="syntax"></a>Syntaxe

```
class CComDynamicUnkArray
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|Konstruktor Inicializuje hodnoty kolekce na HODNOTU NULL a velikost kolekce na nulu.|
|[CComDynamicUnkArray::~CComDynamicUnkArray](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComDynamicUnkArray::Přidat](#add)|Volání této metody `IUnknown` přidat ukazatel pole.|
|[CComDynamicUnkArray::begin](#begin)|Vrátí ukazatel na `IUnknown` první ukazatel v kolekci.|
|[CComDynamicUnkArray::vymazat](#clear)|Vyprázdní pole.|
|[CComDynamicUnkArray::konec](#end)|Vrátí ukazatel na jeden `IUnknown` za poslední ukazatel v kolekci.|
|[CComDynamicUnkArray::Získat](#getat)|Načte prvek v zadaném indexu.|
|[CComDynamicUnkArray::GetCookie](#getcookie)|Volání této metody získat cookie přidružené `IUnknown` k danému ukazateli.|
|[CComDynamicUnkArray::GetSize](#getsize)|Vrátí délku pole.|
|[CComDynamicUnkArray::GetUnknown](#getunknown)|Volání této metody `IUnknown` získat ukazatel přidružený k dané cookie.|
|[CComDynamicUnkArray::Odebrat](#remove)|Volání této metody `IUnknown` odebrat ukazatel z pole.|

## <a name="remarks"></a>Poznámky

`CComDynamicUnkArray`obsahuje dynamicky přidělené `IUnknown` pole ukazatelů, z nichž každé je rozhraním v spojovacím bodě. `CComDynamicUnkArray`lze použít jako parametr pro třídu šablony [IConnectionPointImpl.](../../atl/reference/iconnectionpointimpl-class.md)

Metody `CComDynamicUnkArray` [begin](#begin) a [end](#end) lze použít ke smyčku přes všechny spojovací body (například při je aktivována událost).

Podrobnosti o automatizaci vytváření proxy bodů připojení naleznete v části [Přidání spojovacích bodů do objektu.](../../atl/adding-connection-points-to-an-object.md)

> [!NOTE]
> **Poznámka:** Třída `CComDynamicUnkArray` je používána průvodcem **Přidat třídu** při vytváření ovládacího prvku, který má spojovací body. Chcete-li zadat počet spojovacích bodů ručně, `CComDynamicUnkArray` změňte `CComUnkArray<` odkaz z *na n* `>`, kde *n* je požadovaný počet spojovacích bodů.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ccomdynamicunkarrayadd"></a><a name="add"></a>CComDynamicUnkArray::Přidat

Volání této metody `IUnknown` přidat ukazatel pole.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
Ukazatel, `IUnknown` který chcete přidat do pole.

### <a name="return-value"></a>Návratová hodnota

Vrátí soubor cookie přidružený k nově přidanému ukazateli.

## <a name="ccomdynamicunkarraybegin"></a><a name="begin"></a>CComDynamicUnkArray::begin

Vrátí ukazatel na začátek kolekce `IUnknown` ukazatelů rozhraní.

```
IUnknown**
    begin();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `IUnknown` ukazatel rozhraní.

### <a name="remarks"></a>Poznámky

Kolekce obsahuje ukazatele na rozhraní uložená `IUnknown`místně jako . Přetypovat `IUnknown` každé rozhraní na skutečný typ rozhraní a pak volat přes něj. Není nutné nejprve dotazovat na rozhraní.

Před použitím `IUnknown` rozhraní byste měli zkontrolovat, zda není null.

## <a name="ccomdynamicunkarrayclear"></a><a name="clear"></a>CComDynamicUnkArray::vymazat

Vyprázdní pole.

```cpp
void clear();
```

## <a name="ccomdynamicunkarrayccomdynamicunkarray"></a><a name="ccomdynamicunkarray"></a>CComDynamicUnkArray::CComDynamicUnkArray

Konstruktor

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>Poznámky

Nastaví velikost kolekce na nulu a inicializuje hodnoty na HODNOTU NULL. Destruktor uvolní kolekce, v případě potřeby.

## <a name="ccomdynamicunkarrayccomdynamicunkarray"></a><a name="dtor"></a>CComDynamicUnkArray::~CComDynamicUnkArray

Destruktor.

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>Poznámky

Uvolní prostředky přidělené konstruktorem třídy.

## <a name="ccomdynamicunkarrayend"></a><a name="end"></a>CComDynamicUnkArray::konec

Vrátí ukazatel na jeden `IUnknown` za poslední ukazatel v kolekci.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `IUnknown` ukazatel rozhraní.

## <a name="ccomdynamicunkarraygetat"></a><a name="getat"></a>CComDynamicUnkArray::Získat

Načte prvek v zadaném indexu.

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index prvku načíst.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní [IUnknown.](/windows/win32/api/unknwn/nn-unknwn-iunknown)

## <a name="ccomdynamicunkarraygetcookie"></a><a name="getcookie"></a>CComDynamicUnkArray::GetCookie

Volání této metody získat cookie přidružené `IUnknown` k danému ukazateli.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Parametry

*ppNajít*<br/>
Ukazatel, `IUnknown` pro který je vyžadován přidružený soubor cookie.

### <a name="return-value"></a>Návratová hodnota

Vrátí soubor cookie `IUnknown` přidružený k ukazateli `IUnknown` nebo nulu, pokud není nalezen žádný odpovídající ukazatel.

### <a name="remarks"></a>Poznámky

Pokud existuje více než jedna `IUnknown` instance stejného ukazatele, tato funkce vrátí soubor cookie pro první.

## <a name="ccomdynamicunkarraygetsize"></a><a name="getsize"></a>CComDynamicUnkArray::GetSize

Vrátí délku pole.

```
int GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka pole.

## <a name="ccomdynamicunkarraygetunknown"></a><a name="getunknown"></a>CComDynamicUnkArray::GetUnknown

Volání této metody `IUnknown` získat ukazatel přidružený k dané cookie.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie*<br/>
Soubor cookie, pro `IUnknown` který je vyžadován přidružený ukazatel.

### <a name="return-value"></a>Návratová hodnota

Vrátí `IUnknown` ukazatel nebo NULL, pokud není nalezen žádný odpovídající soubor cookie.

## <a name="ccomdynamicunkarrayremove"></a><a name="remove"></a>CComDynamicUnkArray::Odebrat

Volání této metody `IUnknown` odebrat ukazatel z pole.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie*<br/>
Soubor cookie odkazující na ukazatel, který `IUnknown` má být odebrán z pole.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je ukazatel odebrán; jinak FALSE.

## <a name="see-also"></a>Viz také

[Třída CComUnkArray](../../atl/reference/ccomunkarray-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
