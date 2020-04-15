---
title: atomic_flag – struktura
ms.date: 11/04/2016
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
ms.openlocfilehash: ad4b6dcaf6db1a8abe5b81b4d630e84b54fbaa63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376873"
---
# <a name="atomic_flag-structure"></a>atomic_flag – struktura

Popisuje objekt, který atomicky nastaví a vymaže **bool** příznak. Operace na atomické příznaky jsou vždy bez zámku.

## <a name="syntax"></a>Syntaxe

```cpp
struct atomic_flag;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Jasné](#clear)|Nastaví uložený příznak na **hodnotu false**.|
|[test_and_set](#test_and_set)|Nastaví uložený příznak na **hodnotu true** a vrátí počáteční hodnotu příznaku.|

## <a name="remarks"></a>Poznámky

`atomic_flag`objekty mohou být předány nečlenským funkcím [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set)a [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit). Mohou být inicializovány `ATOMIC_FLAG_INIT`pomocí hodnoty .

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<atomová>

**Obor názvů:** std

## <a name="atomic_flagclear"></a><a name="clear"></a>atomic_flag::vymazat

Nastaví **příznak bool,** `*this` který je uložen v **false**, v rámci [zadaného memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení.

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parametry

*Objednávky*\
Memory_order [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flagtest_and_set"></a><a name="test_and_set"></a>atomic_flag::test_and_set

Nastaví **příznak bool,** `*this` který je uložen v **aplikaci true**, v rámci zadaného [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení.

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parametry

*Objednávky*\
Memory_order [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Počáteční hodnota příznaku, který `*this`je uložen v aplikaci .

## <a name="see-also"></a>Viz také

[\<atomové>](../standard-library/atomic.md)
