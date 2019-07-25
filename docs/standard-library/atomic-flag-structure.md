---
title: atomic_flag – struktura
ms.date: 11/04/2016
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
ms.openlocfilehash: 36944c3c3bdc58272d87bbcdfb119d1c52c43995
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447408"
---
# <a name="atomicflag-structure"></a>atomic_flag – struktura

Popisuje objekt, který atomicky nastavuje a maže příznak **bool** . Operace na atomických příznacích jsou vždycky bez zámku.

## <a name="syntax"></a>Syntaxe

```cpp
struct atomic_flag;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[jejich](#clear)|Nastaví uložený příznak na **false**.|
|[test_and_set](#test_and_set)|Nastaví uložený příznak na **hodnotu true** a vrátí počáteční hodnotu příznaku.|

## <a name="remarks"></a>Poznámky

`atomic_flag`objekty mohou být předány nečlenským funkcím [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set)a [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit). Lze je inicializovat pomocí hodnoty `ATOMIC_FLAG_INIT`.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<atomická >

**Obor názvů:** std

## <a name="clear"></a>atomic_flag:: Clear

Nastaví příznak **bool** , který je uložen v `*this` **hodnotě false**v rámci zadaného omezení [memory_order](../standard-library/atomic-enums.md#memory_order_enum) .

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parametry

*Za*\
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="test_and_set"></a>atomic_flag::test_and_set

Nastaví příznak **bool** , který je uložen v `*this` **hodnotě true**v rámci zadaného omezení [memory_order](../standard-library/atomic-enums.md#memory_order_enum) .

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parametry

*Za*\
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Počáteční hodnota příznaku, který je uložen v `*this`.

## <a name="see-also"></a>Viz také:

[\<atomická >](../standard-library/atomic.md)
