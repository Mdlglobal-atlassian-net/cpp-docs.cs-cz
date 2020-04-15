---
title: duration_values – struktura
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
ms.openlocfilehash: e2c03b4540ea5f89843562d1310b71635b3bc259
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368749"
---
# <a name="duration_values-structure"></a>duration_values – struktura

Poskytuje specifické hodnoty [duration](../standard-library/duration-class.md) pro `Rep`parametr šablony doby trvání .

## <a name="syntax"></a>Syntaxe

```cpp
template <class Rep>
struct duration_values;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Max](#max)|Statická. Určuje horní limit pro hodnotu `Rep`typu .|
|[Min](#min)|Statická. Určuje dolní limit pro hodnotu `Rep`typu .|
|[Nula](#zero)|Statická. Vrací objekt `Rep(0)`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<chrono>

**Obor názvů:** std::chrono

## <a name="duration_valuesmax"></a><a name="max"></a>duration_values::max

Statická metoda, která vrací horní `Ref`mez pro hodnoty typu .

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>Návratová hodnota

Ve skutečnosti `numeric_limits<Rep>::max()`vrátí .

### <a name="remarks"></a>Poznámky

Pokud `Rep` je uživatelem definovaný typ, musí být vrácená hodnota větší než [duration_values::nula](#zero).

## <a name="duration_valuesmin"></a><a name="min"></a>duration_values::min

Statická metoda, která vrací dolní `Ref`mez pro hodnoty typu .

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>Návratová hodnota

Ve skutečnosti `numeric_limits<Rep>::lowest()`vrátí .

### <a name="remarks"></a>Poznámky

Pokud `Rep` je uživatelem definovaný typ, musí být vrácená hodnota menší nebo rovna [duration_values::nula](#zero).

## <a name="duration_valueszero"></a><a name="zero"></a>duration_values::nula

Vrací objekt `Rep(0)`.

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>Poznámky

Pokud `Rep` je uživatelem definovaný typ, musí vrácená hodnota představovat aditivní nekonečno.

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
