---
title: '&lt;hash_set –&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <hash_set>
- std::<hash_set>
dev_langs:
- C++
helpviewer_keywords:
- hash_set header
ms.assetid: 6b556967-c808-4869-9b4d-f9e030864435
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 909944726124a6a3a87ba60ea790945d67ad17a9
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="lthashsetgt"></a>&lt;hash_set&gt;

> [!NOTE]
> Tuto hlavičku je zastaralé. Alternativou je [< unordered_set >](../standard-library/unordered-set.md).

Definuje hash_set třídy šablony kontejneru a hash_multiset a jejich podpůrné šablony.

## <a name="syntax"></a>Syntaxe

```cpp
#include <hash_set>

```

## <a name="remarks"></a>Poznámky

### <a name="operators"></a>Operátory

|Hash_set – verze|Hash_multiset – verze|Popis|
|-----------------------|----------------------------|-----------------|
|[Operator! = (hash_set)](../standard-library/hash-set-operators.md#op_neq)|[Operator! = (hash_multiset)](../standard-library/hash-set-operators.md#op_neq)|Testy, pokud hash_set nebo hash_multiset objekt na levé straně operátor není rovno hash_set nebo hash_multiset objekt na pravé straně.|
|[Operator == (hash_set)](../standard-library/hash-set-operators.md#op_eq_eq)|[Operator == (hash_multiset)](../standard-library/hash-set-operators.md#op_eq_eq)|Testy, pokud hash_set nebo hash_multiset objekt na levé straně operátoru rovná hash_set nebo hash_multiset objekt na pravé straně.|

### <a name="specialized-template-functions"></a>Specializované funkce šablon

|Hash_set – verze|Hash_multiset – verze|Popis|
|-----------------------|----------------------------|-----------------|
|[swap (hash_set)](../standard-library/hash-set-functions.md#swap)|[swap (hash_multiset)](../standard-library/hash-set-functions.md#swap_hash_multiset)|Elementy dva hash_sets nebo hash_multisets výměny.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[hash_compare – třída](../standard-library/hash-compare-class.md)|Popisuje objekt, který můžete použít žádné kontejnery asociativní hash – hash_map, hash_multimap, hash_set, nebo hash_multiset – ve výchozím nastavení **vlastnosti** parametr objekt pořadí a hodnoty hash elementy obsahují.|
|[hash_set – třída](../standard-library/hash-set-class.md)|Používá pro ukládání a rychlé načítání dat z kolekce, ve kterém jsou jedinečné hodnoty elementů obsažených a slouží jako hodnoty klíče.|
|[hash_multiset – třída](../standard-library/hash-multiset-class.md)|Používá pro ukládání a rychlé načítání dat z kolekce, ve kterém jsou jedinečné hodnoty elementů obsažených a slouží jako hodnoty klíče.|

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
