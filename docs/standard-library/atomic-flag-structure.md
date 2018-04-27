---
title: atomic_flag – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
dev_langs:
- C++
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1f36164427f7cbc1cea9fda5f7e4d20896323d08
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="atomicflag-structure"></a>atomic_flag – struktura

Popisuje, objektu, která atomicky nastaví a vymaže `bool` příznak. Operace na atomic příznaky jsou vždy bez zámku.

## <a name="syntax"></a>Syntaxe

```cpp
struct atomic_flag;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Zrušte zaškrtnutí](#clear)|Nastaví příznak uložené na `false`.|
|[test_and_set](#test_and_set)|Nastaví příznak uložené na `true` a vrátí hodnotu počáteční příznak.|

## <a name="remarks"></a>Poznámky

`atomic_flag` objekty lze předat jiné členské funkce [atomic_flag_clear –](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit –](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set –](../standard-library/atomic-functions.md#atomic_flag_test_and_set), a [atomic _flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit). Může být inicializovat pomocí hodnoty `ATOMIC_FLAG_INIT`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<atomic >

**Namespace:** – std

## <a name="clear"></a>  atomic_flag::clear –

Nastaví `bool` příznak, který je uložen v `*this` k `false`, v rámci zadaného [memory_order –](../standard-library/atomic-enums.md#memory_order_enum) omezení.

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parametry

`Order` A [memory_order –](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="test_and_set"></a>  atomic_flag::test_and_set –

Nastaví `bool` příznak, který je uložen v `*this` k `true`, v rámci zadaného [memory_order –](../standard-library/atomic-enums.md#memory_order_enum) omezení.

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parametry

`Order` A [memory_order –](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Počáteční hodnota příznak, který je uložen v `*this`.

## <a name="see-also"></a>Viz také

[\<Atomic >](../standard-library/atomic.md)<br/>
