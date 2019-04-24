---
title: Ccomdynamicunkarray – třída
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
ms.openlocfilehash: 39f137f199db1d7519801c19375baea6cd08db93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259479"
---
# <a name="ccomdynamicunkarray-class"></a>Ccomdynamicunkarray – třída

Tato třída obsahuje pole z `IUnknown` ukazatele.

## <a name="syntax"></a>Syntaxe

```
class CComDynamicUnkArray
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|Konstruktor Inicializuje kolekci hodnoty, které mají hodnotu NULL a velikosti kolekce na nulu.|
|[CComDynamicUnkArray::~CComDynamicUnkArray](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComDynamicUnkArray::Add](#add)|Voláním této metody lze přidat `IUnknown` ukazatel na pole.|
|[CComDynamicUnkArray::begin](#begin)|Vrací ukazatel na první `IUnknown` ukazatel v kolekci.|
|[CComDynamicUnkArray::clear](#clear)|Vyprázdní pole.|
|[CComDynamicUnkArray::end](#end)|Vrací ukazatel na jedno místo za posledním `IUnknown` ukazatel v kolekci.|
|[CComDynamicUnkArray::GetAt](#getat)|Načte prvek v zadaném indexu.|
|[CComDynamicUnkArray::GetCookie](#getcookie)|Volejte tuto metodu za účelem získání souborů cookie, přidružené danou `IUnknown` ukazatele.|
|[CComDynamicUnkArray::GetSize](#getsize)|Vrátí délku pole.|
|[CComDynamicUnkArray::GetUnknown](#getunknown)|Volejte tuto metodu za účelem získání `IUnknown` ukazatel přidružený k daném souboru cookie.|
|[CComDynamicUnkArray::Remove](#remove)|Volejte tuto metodu za účelem odebrání `IUnknown` ukazatele z pole.|

## <a name="remarks"></a>Poznámky

`CComDynamicUnkArray` obsahuje dynamicky přiřazeného pole `IUnknown` ukazatele, každý bod rozhraní připojení. `CComDynamicUnkArray` lze použít jako parametr [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) šablony třídy.

`CComDynamicUnkArray` Metody [začít](#begin) a [end](#end) lze použít k vytvoření smyčky přes všechny body připojení (například když se aktivuje událost).

Zobrazit [přidání bodů připojení objektu](../../atl/adding-connection-points-to-an-object.md) podrobnosti k automatizaci vytváření připojení bodu proxy servery.

> [!NOTE]
> **Poznámka:** třídy `CComDynamicUnkArray` používá **přidat třídu** Průvodce při vytváření ovládacího prvku, který má spojovací body. Pokud chcete určit, kolik bodů připojení ručně, změňte odkazy z `CComDynamicUnkArray` k `CComUnkArray<` *n* `>`, kde *n* je počet bodů připojení povinné.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="add"></a>  CComDynamicUnkArray::Add

Voláním této metody lze přidat `IUnknown` ukazatel na pole.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
`IUnknown` Ukazatel na Přidat do pole.

### <a name="return-value"></a>Návratová hodnota

Vrátí přidružený ukazatel na nově přidaný soubor cookie.

##  <a name="begin"></a>  CComDynamicUnkArray::begin

Vrací ukazatel na začátek kolekce `IUnknown` ukazatele rozhraní.

```
IUnknown**
    begin();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `IUnknown` ukazatel rozhraní.

### <a name="remarks"></a>Poznámky

Kolekce obsahuje odkazy na rozhraní místně uložená jako `IUnknown`. Každý přetypování `IUnknown` rozhraní na typ skutečné rozhraní a pak přes ni volat. Dotaz na rozhraní nejprve nepotřebujete.

Před použitím `IUnknown` rozhraní, zkontrolujte, že není NULL.

##  <a name="clear"></a>  CComDynamicUnkArray::clear

Vyprázdní pole.

```
void clear();
```

##  <a name="ccomdynamicunkarray"></a>  CComDynamicUnkArray::CComDynamicUnkArray

Konstruktor

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>Poznámky

Nastaví velikost kolekce na nulu a inicializuje hodnoty, které mají hodnotu NULL. Destruktor uvolní kolekce, v případě potřeby.

##  <a name="dtor"></a>  CComDynamicUnkArray::~CComDynamicUnkArray

Destruktor.

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>Poznámky

Uvolní prostředky přidělené pomocí konstruktoru třídy.

##  <a name="end"></a>  CComDynamicUnkArray::end

Vrací ukazatel na jedno místo za posledním `IUnknown` ukazatel v kolekci.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `IUnknown` ukazatel rozhraní.

##  <a name="getat"></a>  CComDynamicUnkArray::GetAt

Načte prvek v zadaném indexu.

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index prvku, který chcete načíst.

### <a name="return-value"></a>Návratová hodnota

Ukazatel [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) rozhraní.

##  <a name="getcookie"></a>  CComDynamicUnkArray::GetCookie

Volejte tuto metodu za účelem získání souborů cookie, přidružené danou `IUnknown` ukazatele.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Parametry

*ppFind*<br/>
`IUnknown` Ukazatel, pro který je vyžadován přidružený soubor cookie.

### <a name="return-value"></a>Návratová hodnota

Vrátí soubor cookie, přidružené `IUnknown` ukazatel nebo nula, pokud neexistuje odpovídající `IUnknown` nachází ukazatelem.

### <a name="remarks"></a>Poznámky

Pokud existuje více než jednu instanci stejného `IUnknown` ukazatele, tato funkce vrátí soubor cookie pro první z nich.

##  <a name="getsize"></a>  CComDynamicUnkArray::GetSize

Vrátí délku pole.

```
int GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka pole.

##  <a name="getunknown"></a>  CComDynamicUnkArray::GetUnknown

Volejte tuto metodu za účelem získání `IUnknown` ukazatel přidružený k daném souboru cookie.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie*<br/>
Soubor cookie, pro kterou přidruženého `IUnknown` ukazatel je povinný.

### <a name="return-value"></a>Návratová hodnota

Vrátí `IUnknown` ukazatel nebo hodnota NULL, pokud není nalezen žádný odpovídající soubor cookie.

##  <a name="remove"></a>  CComDynamicUnkArray::Remove

Volejte tuto metodu za účelem odebrání `IUnknown` ukazatele z pole.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie*<br/>
Odkazování na soubor cookie `IUnknown` ukazatel na odebrat z pole.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud se odebere ukazatele; v opačném případě FALSE.

## <a name="see-also"></a>Viz také:

[CComUnkArray – třída](../../atl/reference/ccomunkarray-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
