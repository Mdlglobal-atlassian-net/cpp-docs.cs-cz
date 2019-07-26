---
title: duration_values – struktura
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
ms.openlocfilehash: ba4b202a5c8c6da742ac884bf58a5b8c55373d14
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454293"
---
# <a name="durationvalues-structure"></a>duration_values – struktura

Poskytuje konkrétní hodnoty pro parametr [](../standard-library/duration-class.md) `Rep`šablony Duration.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Rep>
struct duration_values;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[max](#max)|Tras. Určuje horní limit hodnoty typu `Rep`.|
|[dlouhé](#min)|Tras. Určuje dolní limit hodnoty typu `Rep`.|
|[vynulujte](#zero)|Tras. Vrátí `Rep(0)`.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<Chrono >

**Obor názvů:** std:: chrono

## <a name="max"></a>duration_values:: max

Statická metoda, která vrátí horní mez pro hodnoty typu `Ref`.

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>Návratová hodnota

V důsledku toho vrátí `numeric_limits<Rep>::max()`.

### <a name="remarks"></a>Poznámky

Když `Rep` je uživatelem definovaný typ, vrácená hodnota musí být větší než [duration_values:: Zero](#zero).

## <a name="min"></a>duration_values:: min

Statická metoda, která vrátí dolní mez pro hodnoty typu `Ref`.

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>Návratová hodnota

V důsledku toho vrátí `numeric_limits<Rep>::lowest()`.

### <a name="remarks"></a>Poznámky

Když `Rep` je uživatelem definovaný typ, vrácená hodnota musí být menší nebo rovna [duration_values:: Zero](#zero).

## <a name="zero"></a>duration_values:: Zero

Vrátí `Rep(0)`.

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>Poznámky

Když `Rep` je uživatelem definovaný typ, návratová hodnota musí představovat nekonečno pro doplňkové látky.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
