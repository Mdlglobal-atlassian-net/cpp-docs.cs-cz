---
title: Ccomunkarray – třída
ms.date: 11/04/2016
f1_keywords:
- CComUnkArray
- ATLCOM/ATL::CComUnkArray
- ATLCOM/ATL::CComUnkArray::CComUnkArray
- ATLCOM/ATL::CComUnkArray::Add
- ATLCOM/ATL::CComUnkArray::begin
- ATLCOM/ATL::CComUnkArray::end
- ATLCOM/ATL::CComUnkArray::GetCookie
- ATLCOM/ATL::CComUnkArray::GetUnknown
- ATLCOM/ATL::CComUnkArray::Remove
helpviewer_keywords:
- connection points [C++], managing
- CComUnkArray class
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
ms.openlocfilehash: 4577e77ac71bbb2e65c8c6168d0d28d5765d551f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550251"
---
# <a name="ccomunkarray-class"></a>Ccomunkarray – třída

Tato třída obsahuje `IUnknown` ukazatele a je určená pro použití jako parametr, který se [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) šablony třídy.

## <a name="syntax"></a>Syntaxe

```
template<unsigned int nMaxSize>
class CComUnkArray
```

#### <a name="parameters"></a>Parametry

*nMaxSize*<br/>
Maximální počet `IUnknown` ukazatele, které se můžou uchovávat ve statickém poli.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComUnkArray::CComUnkArray](#ccomunkarray)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComUnkArray::Add](#add)|Voláním této metody lze přidat `IUnknown` ukazatel na pole.|
|[CComUnkArray::begin](#begin)|Vrací ukazatel na první `IUnknown` ukazatel v kolekci.|
|[CComUnkArray::end](#end)|Vrací ukazatel na jedno místo za posledním `IUnknown` ukazatel v kolekci.|
|[CComUnkArray::GetCookie](#getcookie)|Volejte tuto metodu za účelem získání souborů cookie, přidružené danou `IUnknown` ukazatele.|
|[CComUnkArray::GetUnknown](#getunknown)|Volejte tuto metodu za účelem získání `IUnknown` ukazatel přidružený k daném souboru cookie.|
|[CComUnkArray::Remove](#remove)|Volejte tuto metodu za účelem odebrání `IUnknown` ukazatele z pole.|

## <a name="remarks"></a>Poznámky

`CComUnkArray` obsahuje pevný počet `IUnknown` ukazatele, každý bod rozhraní připojení. `CComUnkArray` lze použít jako parametr [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) šablony třídy. `CComUnkArray<1>` je specializací šablony `CComUnkArray` , která je optimalizována pro jedno připojení bodu.

`CComUnkArray` Metody [začít](#begin) a [end](#end) lze použít k vytvoření smyčky přes všechny body připojení (například když se aktivuje událost).

Zobrazit [přidání bodů připojení objektu](../../atl/adding-connection-points-to-an-object.md) podrobnosti k automatizaci vytváření připojení bodu proxy servery.

> [!NOTE]
> **Poznámka:** třídy [ccomdynamicunkarray –](../../atl/reference/ccomdynamicunkarray-class.md) používá **přidat třídu** Průvodce při vytváření ovládacího prvku, který má spojovací body. Pokud chcete určit, kolik bodů připojení ručně, změňte odkazy z `CComDynamicUnkArray` k `CComUnkArray<` *n* `>`, kde *n* je počet bodů připojení povinné.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="add"></a>  CComUnkArray::Add

Voláním této metody lze přidat `IUnknown` ukazatel na pole.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
Voláním této metody lze přidat `IUnknown` ukazatel na pole.

### <a name="return-value"></a>Návratová hodnota

Vrátí přidružený ukazatel na nově přidané nebo 0, pokud pole není dostatečně velký, aby obsahovat nový ukazatel souboru cookie.

##  <a name="begin"></a>  CComUnkArray::begin

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

##  <a name="ccomunkarray"></a>  CComUnkArray::CComUnkArray

Konstruktor

```
CComUnkArray();
```

### <a name="remarks"></a>Poznámky

Nastaví kolekci pro uchování `nMaxSize` `IUnknown` ukazatele a inicializuje ukazatele na hodnotu NULL.

##  <a name="end"></a>  CComUnkArray::end

Vrací ukazatel na jedno místo za posledním `IUnknown` ukazatel v kolekci.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `IUnknown` ukazatel rozhraní.

### <a name="remarks"></a>Poznámky

`CComUnkArray` Metody `begin` a `end` je možné projít všechny body připojení, například když se aktivuje událost.

[!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]

##  <a name="getcookie"></a>  CComUnkArray::GetCookie

Volejte tuto metodu za účelem získání souborů cookie, přidružené danou `IUnknown` ukazatele.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Parametry

*ppFind*<br/>
`IUnknown` Ukazatel, pro který je vyžadován přidružený soubor cookie.

### <a name="return-value"></a>Návratová hodnota

Vrátí soubor cookie, přidružené `IUnknown` ukazatele, nebo 0, pokud neexistuje odpovídající `IUnknown` nachází ukazatelem.

### <a name="remarks"></a>Poznámky

Pokud existuje více než jednu instanci stejného `IUnknown` ukazatele, tato funkce vrátí soubor cookie pro první z nich.

##  <a name="getunknown"></a>  CComUnkArray::GetUnknown

Volejte tuto metodu za účelem získání `IUnknown` ukazatel přidružený k daném souboru cookie.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie*<br/>
Soubor cookie, pro kterou přidruženého `IUnknown` ukazatel je povinný.

### <a name="return-value"></a>Návratová hodnota

Vrátí `IUnknown` ukazatel nebo hodnota NULL, pokud není nalezen žádný odpovídající soubor cookie.

##  <a name="remove"></a>  CComUnkArray::Remove

Volejte tuto metodu za účelem odebrání `IUnknown` ukazatele z pole.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie*<br/>
Odkazování na soubor cookie `IUnknown` ukazatel na odebrat z pole.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud ukazatel myši je odebrána, FALSE, jinak.

## <a name="see-also"></a>Viz také

[CComDynamicUnkArray – třída](../../atl/reference/ccomdynamicunkarray-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
