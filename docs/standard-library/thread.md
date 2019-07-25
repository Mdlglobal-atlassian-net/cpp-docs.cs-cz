---
title: '&lt;thread&gt;'
ms.date: 11/04/2016
f1_keywords:
- <thread>
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
ms.openlocfilehash: 7053402dfb566f10c7be4c0eebaef40f3d371f43
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460078"
---
# <a name="ltthreadgt"></a>&lt;thread&gt;

Zahrňte standardní > \<podprocesu hlavičky pro definování **vlákna** třídy a různých podpůrných funkcí.

## <a name="syntax"></a>Syntaxe

```cpp
#include <thread>
```

## <a name="remarks"></a>Poznámky

> [!NOTE]
> V kódu, který je zkompilován pomocí **/CLR**, je tato hlavička zablokována.

`__STDCPP_THREADS__` Makro je definováno jako nenulová hodnota, která označuje, že vlákna jsou podporována touto hlavičkou.

## <a name="members"></a>Členové

### <a name="public-classes"></a>Veřejné třídy

|Name|Popis|
|----------|-----------------|
|[thread – třída](../standard-library/thread-class.md)|Definuje objekt, který se používá ke sledování a správě vlákna provádění v aplikaci.|

### <a name="public-structures"></a>Veřejné struktury

|Name|Popis|
|----------|-----------------|
|[hash – struktura (standardní knihovna C++)](../standard-library/hash-structure-stl.md)|Definuje členskou funkci, která vrací hodnotu, která je jednoznačně určena `thread::id`hodnotou. Členská funkce definuje funkci [hash](../standard-library/hash-class.md) , která je vhodná pro mapování hodnot typu `thread::id` na distribuci hodnot indexu.|

### <a name="public-functions"></a>Veřejné funkce

|Name|Popis|
|----------|-----------------|
|[get_id](../standard-library/thread-functions.md#get_id)|Jednoznačně identifikuje aktuální vlákno provádění.|
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|Blokuje volající vlákno.|
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|Blokuje volající vlákno alespoň do zadaného času.|
|[swap](../standard-library/thread-functions.md#swap)|Vyměňuje stavy dvou objektů **vlákna** .|
|[yield](../standard-library/thread-functions.md#yield)|Signalizuje operačnímu systému, aby spouštěl další vlákna, i v případě, že aktuální vlákno obvykle pokračuje v běhu.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[operator > = – operátor](../standard-library/thread-operators.md#op_gt_eq)|Určuje, zda `thread::id` je jeden objekt větší nebo roven jinému objektu.|
|[operator > – operátor](../standard-library/thread-operators.md#op_gt)|Určuje, zda `thread::id` je jeden objekt větší než jiný.|
|[operator < = – operátor](../standard-library/thread-operators.md#op_lt_eq)|Určuje, zda `thread::id` je jeden objekt menší nebo roven jinému objektu.|
|[operator < – operátor](../standard-library/thread-operators.md#op_lt)|Určuje, zda `thread::id` je jeden objekt menší než jiný.|
|[operator! = – operátor](../standard-library/thread-operators.md#op_neq)|Porovná `thread::id` dva objekty pro nerovnost.|
|[operator = = – operátor](../standard-library/thread-operators.md#op_eq_eq)|Porovná `thread::id` dva objekty pro rovnost.|
|[operator < – operátor <](../standard-library/thread-operators.md#op_lt_lt)|Vloží textovou reprezentaci `thread::id` objektu do datového proudu.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
