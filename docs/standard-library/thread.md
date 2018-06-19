---
title: '&lt;vlákno&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <thread>
dev_langs:
- C++
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5558f1e7998cca1efd64fbc5ee0ad39cc40ee2a6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858611"
---
# <a name="ltthreadgt"></a>&lt;thread&gt;

Zahrnují standardní hlavičku \<vlákno > pro definování třídy `thread` a různé podpůrné funkce.

## <a name="syntax"></a>Syntaxe

```cpp
#include <thread>
```

## <a name="remarks"></a>Poznámky

> [!NOTE]
> V kódu, který se zkompiluje pomocí **/CLR**, tuto hlavičku je blokovaný.

`__STDCPP_THREADS__` Makro je definován jako nenulovou hodnotu indikující, že vláken podporuje tuto hlavičku.

## <a name="members"></a>Členové

### <a name="public-classes"></a>Veřejné třídy

|Název|Popis|
|----------|-----------------|
|[thread – třída](../standard-library/thread-class.md)|Definuje objekt, který se používá k sledovat a spravovat vlákno při provádění v aplikaci.|

### <a name="public-structures"></a>Veřejné struktury

|Název|Popis|
|----------|-----------------|
|[hash – struktura (standardní knihovna C++)](../standard-library/hash-structure-stl.md)|Definuje členské funkce, která vrátí hodnotu, která je jednoznačně dáno `thread::id`. Definuje – členská funkce [hash](../standard-library/hash-class.md) funkce, který je vhodný pro mapování hodnoty typu `thread::id` k distribučnímu index hodnot.|

### <a name="public-functions"></a>Veřejné funkce

|Název|Popis|
|----------|-----------------|
|[get_id](../standard-library/thread-functions.md#get_id)|Jednoznačně identifikuje aktuální vlákno provádění.|
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|Blokuje volající vlákno.|
|[sleep_until –](../standard-library/thread-functions.md#sleep_until)|Volající vlákno blokuje alespoň do zadané doby.|
|[Swap](../standard-library/thread-functions.md#swap)|Výměny stavy dva `thread` objekty.|
|[yield](../standard-library/thread-functions.md#yield)|Signály operačního systému spustit jiná vlákna i v případě, že aktuální vlákno by normálně nadále fungoval.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[Operator > = – operátor](../standard-library/thread-operators.md#op_gt_eq)|Určuje, zda jeden `thread::id` je větší než nebo rovna hodnotě jiný objekt.|
|[Operator > – operátor](../standard-library/thread-operators.md#op_gt)|Určuje, zda jeden `thread::id` je větší než druhý objekt.|
|[Operator < = – operátor](../standard-library/thread-operators.md#op_lt_eq)|Určuje, zda jeden `thread::id` objektu je menší než nebo rovna do jiného.|
|[Operator < – operátor](../standard-library/thread-operators.md#op_lt)|Určuje, zda jeden `thread::id` objektu je menší než jiné.|
|[Operator! = – operátor](../standard-library/thread-operators.md#op_neq)|Porovná dva `thread::id` objekty nerovnost.|
|[Operator == – operátor](../standard-library/thread-operators.md#op_eq_eq)|Porovná dva `thread::id` objekty rovnosti.|
|[operátor << – operátor](../standard-library/thread-operators.md#op_lt_lt)|Vloží text reprezentace `thread::id` objektu do datového proudu.|

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
