---
title: Třída CComUnkArray
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
ms.openlocfilehash: c1d2f0296394d3979ef4f152e3f902c89adf5b45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327308"
---
# <a name="ccomunkarray-class"></a>Třída CComUnkArray

Tato třída `IUnknown` ukládá ukazatele a je navržena pro použití jako parametr pro třídu šablony [IConnectionPointImpl.](../../atl/reference/iconnectionpointimpl-class.md)

## <a name="syntax"></a>Syntaxe

```
template<unsigned int nMaxSize>
class CComUnkArray
```

#### <a name="parameters"></a>Parametry

*nVelikost Max*<br/>
Maximální počet `IUnknown` ukazatelů, které mohou být drženy ve statickém poli.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CComUnkArray::CComUnkArray](#ccomunkarray)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComUnkArray::Přidat](#add)|Volání této metody `IUnknown` přidat ukazatel pole.|
|[CComUnkArray::begin](#begin)|Vrátí ukazatel na `IUnknown` první ukazatel v kolekci.|
|[CComUnkArray::konec](#end)|Vrátí ukazatel na jeden `IUnknown` za poslední ukazatel v kolekci.|
|[CComUnkArray::GetCookie](#getcookie)|Volání této metody získat cookie přidružené `IUnknown` k danému ukazateli.|
|[CComUnkArray::GetUnknown](#getunknown)|Volání této metody `IUnknown` získat ukazatel přidružený k dané cookie.|
|[CComUnkArray::Odebrat](#remove)|Volání této metody `IUnknown` odebrat ukazatel z pole.|

## <a name="remarks"></a>Poznámky

`CComUnkArray`obsahuje pevný počet `IUnknown` ukazatelů, z nichž každý je rozhraním v spojovacím bodě. `CComUnkArray`lze použít jako parametr pro třídu šablony [IConnectionPointImpl.](../../atl/reference/iconnectionpointimpl-class.md) `CComUnkArray<1>`je specializace `CComUnkArray` šablony, která byla optimalizována pro jeden spojovací bod.

Metody `CComUnkArray` [begin](#begin) a [end](#end) lze použít ke smyčku přes všechny spojovací body (například při je aktivována událost).

Podrobnosti o automatizaci vytváření proxy bodů připojení naleznete v části [Přidání spojovacích bodů do objektu.](../../atl/adding-connection-points-to-an-object.md)

> [!NOTE]
> **Poznámka:** Třída [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md) používá průvodce **přidáním třídy** při vytváření ovládacího prvku, který má spojovací body. Chcete-li zadat počet spojovacích bodů ručně, `CComDynamicUnkArray` změňte `CComUnkArray<` odkaz z *na n* `>`, kde *n* je požadovaný počet spojovacích bodů.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ccomunkarrayadd"></a><a name="add"></a>CComUnkArray::Přidat

Volání této metody `IUnknown` přidat ukazatel pole.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
Volání této metody `IUnknown` přidat ukazatel pole.

### <a name="return-value"></a>Návratová hodnota

Vrátí soubor cookie přidružený k nově přidanému ukazateli nebo 0, pokud pole není dostatečně velké, aby obsahovalo nový ukazatel.

## <a name="ccomunkarraybegin"></a><a name="begin"></a>CComUnkArray::begin

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

## <a name="ccomunkarrayccomunkarray"></a><a name="ccomunkarray"></a>CComUnkArray::CComUnkArray

Konstruktor

```
CComUnkArray();
```

### <a name="remarks"></a>Poznámky

Nastaví kolekci `nMaxSize` `IUnknown` tak, aby uchovávala ukazatele, a inicializuje ukazatele na hodnotu NULL.

## <a name="ccomunkarrayend"></a><a name="end"></a>CComUnkArray::konec

Vrátí ukazatel na jeden `IUnknown` za poslední ukazatel v kolekci.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `IUnknown` ukazatel rozhraní.

### <a name="remarks"></a>Poznámky

Metody `CComUnkArray` `begin` a `end` lze použít ke smyčku přes všechny spojovací body, například při je aktivována událost.

[!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]

## <a name="ccomunkarraygetcookie"></a><a name="getcookie"></a>CComUnkArray::GetCookie

Volání této metody získat cookie přidružené `IUnknown` k danému ukazateli.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Parametry

*ppNajít*<br/>
Ukazatel, `IUnknown` pro který je vyžadován přidružený soubor cookie.

### <a name="return-value"></a>Návratová hodnota

Vrátí soubor cookie `IUnknown` přidružený k ukazateli `IUnknown` nebo 0, pokud není nalezen žádný odpovídající ukazatel.

### <a name="remarks"></a>Poznámky

Pokud existuje více než jedna `IUnknown` instance stejného ukazatele, tato funkce vrátí soubor cookie pro první.

## <a name="ccomunkarraygetunknown"></a><a name="getunknown"></a>CComUnkArray::GetUnknown

Volání této metody `IUnknown` získat ukazatel přidružený k dané cookie.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie*<br/>
Soubor cookie, pro `IUnknown` který je vyžadován přidružený ukazatel.

### <a name="return-value"></a>Návratová hodnota

Vrátí `IUnknown` ukazatel nebo NULL, pokud není nalezen žádný odpovídající soubor cookie.

## <a name="ccomunkarrayremove"></a><a name="remove"></a>CComUnkArray::Odebrat

Volání této metody `IUnknown` odebrat ukazatel z pole.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie*<br/>
Soubor cookie odkazující na ukazatel, který `IUnknown` má být odebrán z pole.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je ukazatel odebrán, jinak NEPRAVDA.

## <a name="see-also"></a>Viz také

[Třída CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
