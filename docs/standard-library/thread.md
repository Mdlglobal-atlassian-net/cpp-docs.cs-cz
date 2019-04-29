---
title: '&lt;thread&gt;'
ms.date: 11/04/2016
f1_keywords:
- <thread>
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
ms.openlocfilehash: 43fb79ceda6de7409e6f93797ce2f4ff213c43ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411978"
---
# <a name="ltthreadgt"></a>&lt;thread&gt;

Zahrnout standardní hlavička \<vlákna > pro definování třídy **vlákno** a různé podpůrné funkce.

## <a name="syntax"></a>Syntaxe

```cpp
#include <thread>
```

## <a name="remarks"></a>Poznámky

> [!NOTE]
> V kódu, který je zkompilován s použitím **/CLR**, tato hlavička se zablokuje.

`__STDCPP_THREADS__` Makro je definováno jako nenulovou hodnotu označující, že toto záhlaví podporuje vlákna.

## <a name="members"></a>Členové

### <a name="public-classes"></a>Veřejné třídy

|Název|Popis|
|----------|-----------------|
|[thread – třída](../standard-library/thread-class.md)|Definuje objekt, který umožňuje sledovat a spravovat vlákno provádění v aplikaci.|

### <a name="public-structures"></a>Veřejné struktury

|Název|Popis|
|----------|-----------------|
|[hash – struktura (standardní knihovna C++)](../standard-library/hash-structure-stl.md)|Definuje členskou funkci, která vrací hodnotu, která jednoznačně určuje `thread::id`. Definuje členskou funkci [hash](../standard-library/hash-class.md) funkce, která je vhodná pro mapování hodnot typu `thread::id` k distribuci hodnot indexu.|

### <a name="public-functions"></a>Veřejné funkce

|Název|Popis|
|----------|-----------------|
|[get_id](../standard-library/thread-functions.md#get_id)|Jednoznačně identifikuje aktuální vlákno provádění.|
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|Blokuje volající vlákno.|
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|Blokuje volající vlákno, alespoň do zadané doby.|
|[swap](../standard-library/thread-functions.md#swap)|Vymění dvě stavy **vlákno** objekty.|
|[yield](../standard-library/thread-functions.md#yield)|Signály ke spuštění jiných vláken operačního systému, i v případě, že aktuální vlákno by obvykle i nadále spouštět.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operator>= Operator](../standard-library/thread-operators.md#op_gt_eq)|Určuje, zda jeden `thread::id` objekt je větší než nebo roven jinému.|
|[Operator > – operátor](../standard-library/thread-operators.md#op_gt)|Určuje, zda jeden `thread::id` je větší než jiný objekt.|
|[operator<= Operator](../standard-library/thread-operators.md#op_lt_eq)|Určuje, zda jeden `thread::id` je objekt menší než nebo rovna do jiného.|
|[Operator < – operátor](../standard-library/thread-operators.md#op_lt)|Určuje, zda jeden `thread::id` je menší než jiný objekt.|
|[Operator! = – operátor](../standard-library/thread-operators.md#op_neq)|Porovná dva `thread::id` objekty nerovnost.|
|[Operator == – operátor](../standard-library/thread-operators.md#op_eq_eq)|Porovná dva `thread::id` objekty pro rovnost.|
|[operátor << – operátor](../standard-library/thread-operators.md#op_lt_lt)|Vloží textové vyjádření `thread::id` objektu do datového proudu.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
