---
title: duration_values – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
dev_langs:
- C++
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a2cba8fd6fe3e4763e05dc0cc897e8a0b968d611
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="durationvalues-structure"></a>duration_values – struktura

Poskytuje konkrétní hodnoty [doba trvání](../standard-library/duration-class.md) parametr šablony `Rep`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Rep>
struct duration_values;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[max](#max)|Statické. Určuje horní limit pro hodnotu typu `Rep`.|
|[Min.](#min)|Statické. Určuje dolní limit pro hodnotu typu `Rep`.|
|[Nula.](#zero)|Statické. Vrátí `Rep(0)`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<typu chrono >

**Namespace:** std::chrono

## <a name="max"></a>  duration_values::max –

Statickou metodu, která vrací horní mez pro hodnoty typu `Ref`.

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>Návratová hodnota

V důsledku toho vrátí `numeric_limits<Rep>::max()`.

### <a name="remarks"></a>Poznámky

Když `Rep` je uživatelsky definovaný typ. Návratová hodnota musí být větší než [duration_values::Zero –](#zero).

## <a name="min"></a>  duration_values::min –

Statickou metodu, která vrací dolní mez pro hodnoty typu `Ref`.

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>Návratová hodnota

V důsledku toho vrátí `numeric_limits<Rep>::lowest()`.

### <a name="remarks"></a>Poznámky

Když `Rep` je uživatelsky definovaný typ. Návratová hodnota musí být menší než nebo rovno [duration_values::Zero –](#zero).

## <a name="zero"></a>  duration_values::Zero –

Vrátí `Rep(0)`.

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>Poznámky

Když `Rep` je uživatelsky definovaný typ. Návratová hodnota musí představovat sčítání nekonečna.

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
