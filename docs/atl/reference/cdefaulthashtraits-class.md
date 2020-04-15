---
title: Třída CDefaultHashTraits
ms.date: 11/04/2016
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
ms.openlocfilehash: 43932092621d44cfc8b07270df92e2765665f23f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327087"
---
# <a name="cdefaulthashtraits-class"></a>Třída CDefaultHashTraits

Tato třída poskytuje statickou funkci pro výpočet hodnot hash.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CDefaultHashTraits
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat, která mají být uložena v kolekci.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDefaultHashTraits::Hash](#hash)|(Statické) Volání této funkce k výpočtu hodnoty hash pro daný prvek.|

## <a name="remarks"></a>Poznámky

Tato třída obsahuje jednu statickou funkci, která vrací hodnotu hash pro daný prvek. Tato třída je využívána [třídou CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md).

Další informace naleznete v tématu [třídy kolekce klíčů ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="cdefaulthashtraitshash"></a><a name="hash"></a>CDefaultHashTraits::Hash

Volání této funkce k výpočtu hodnoty hash pro daný prvek.

```
static ULONG Hash(const T& element) throw();
```

### <a name="parameters"></a>Parametry

*Prvek*<br/>
Prvek.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hash.

### <a name="remarks"></a>Poznámky

Výchozí algoritmus hash je velmi jednoduchý: vrácená hodnota je číslo prvku. Přepsat tuto funkci, pokud je vyžadován složitější algoritmus.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
