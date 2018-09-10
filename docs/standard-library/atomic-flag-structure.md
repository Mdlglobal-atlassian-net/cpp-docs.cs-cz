---
title: atomic_flag – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
dev_langs:
- C++
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f763181424bafc4b8b3af41c135753dbe2f2577b
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110315"
---
# <a name="atomicflag-structure"></a>atomic_flag – struktura

Popisuje objekt, který atomicky Nastaví nebo vymaže **bool** příznak. Operace na atomických příznacích jsou vždy bez zámku.

## <a name="syntax"></a>Syntaxe

```cpp
struct atomic_flag;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Vymazat](#clear)|Nastaví uložený příznak na **false**.|
|[test_and_set](#test_and_set)|Nastaví uložený příznak na **true** a vrátí počáteční hodnotu příznaku.|

## <a name="remarks"></a>Poznámky

`atomic_flag` objekty mohou být předány nečlenské funkce [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set), a [atomic _flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit). Mohou být inicializovány pomocí hodnoty `ATOMIC_FLAG_INIT`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<atomické >

**Namespace:** std

## <a name="clear"></a>  atomic_flag::clear –

Nastaví **bool** příznak, který je uložen v `*this` k **false**, v rámci zadaného [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení.

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parametry

*Pořadí*<br/>
A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="test_and_set"></a>  atomic_flag::test_and_set –

Nastaví **bool** příznak, který je uložen v `*this` k **true**, v rámci zadaného [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení.

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parametry

*Pořadí*<br/>
A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Počáteční hodnota příznaku, která je uložena v `*this`.

## <a name="see-also"></a>Viz také:

[\<Atomic >](../standard-library/atomic.md)<br/>
