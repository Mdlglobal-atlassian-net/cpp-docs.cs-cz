---
title: duration_values – struktura
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
ms.openlocfilehash: bc382bbc408b11cbc18210f3ab944dda39adc8f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653385"
---
# <a name="durationvalues-structure"></a>duration_values – struktura

Poskytuje specifické hodnoty pro [doba trvání](../standard-library/duration-class.md) parametr šablony `Rep`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Rep>
struct duration_values;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[max](#max)|Statické. Určuje horní mez pro hodnotu typu `Rep`.|
|[min](#min)|Statické. Určuje dolní mez pro hodnotu typu `Rep`.|
|[Nula](#zero)|Statické. Vrátí `Rep(0)`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<chrono >

**Namespace:** std::chrono

## <a name="max"></a>  duration_values::max –

Statická metoda, která vrátí horní mez pro hodnoty typu `Ref`.

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>Návratová hodnota

V důsledku toho vrátí `numeric_limits<Rep>::max()`.

### <a name="remarks"></a>Poznámky

Když `Rep` je uživatelem definovaný typ, vrácená hodnota musí být větší než [duration_values::zero](#zero).

## <a name="min"></a>  duration_values::min –

Statická metoda, která vrátí dolní mez pro hodnoty typu `Ref`.

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>Návratová hodnota

V důsledku toho vrátí `numeric_limits<Rep>::lowest()`.

### <a name="remarks"></a>Poznámky

Když `Rep` je uživatelem definovaný typ, vrácená hodnota musí být menší než nebo rovno [duration_values::zero](#zero).

## <a name="zero"></a>  duration_values::Zero

Vrátí `Rep(0)`.

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>Poznámky

Když `Rep` je uživatelem definovaný typ, vrácená hodnota musí představovat aditivní nekonečno.

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
