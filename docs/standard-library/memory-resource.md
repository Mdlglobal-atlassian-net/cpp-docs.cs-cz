---
title: '&lt;memory_resource&gt;'
ms.date: 04/04/2019
f1_keywords:
- <memory_resource>
helpviewer_keywords:
- memory_resource header
ms.openlocfilehash: b5957412d2beff0dc709dc71a77834f13eeacb41
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268156"
---
# <a name="ltmemoryresourcegt"></a>&lt;memory_resource&gt;

Definuje kontejner šablony třídy memory_resource a jeho podpůrných šablon.

## <a name="syntax"></a>Syntaxe

```cpp
#include <memory_resource>
```

## <a name="members"></a>Členové

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator!=](../standard-library/memory-resource-operators.md#op_neq)|Testuje, zda je objekt memory_resource na levé straně operátoru není roven objektu memory_resource na pravé straně.|
|[operator==](../standard-library/memory-resource-operators.md#op_eq_eq)|Testuje, zda objekt memory_resource na levé straně operátoru roven objektu memory_resource na pravé straně.|

### <a name="specialized-template-functions"></a>Specializované funkce šablon

|||
|-|-|
|[polymorphic_allocator](../standard-library/memory-resource-functions.md#poly_alloc)||

### <a name="functions"></a>Funkce

|||
|-|-|
|[get_default_resource](../standard-library/memory-resource-functions.md#get_default)||
|[new_delete_resource](../standard-library/memory-resource-functions.md#new_delete)||
|[null_memory_resource](../standard-library/memory-resource-functions.md#null_memory)||
|[set_default_resource](../standard-library/memory-resource-functions.md#set_default)||

### <a name="classes-and-structs"></a>Třídy a struktury

|||
|-|-|
|[memory_resource třídy](../standard-library/memory-resource-class.md)||
|[monotonic_buffer_resource třídy](../standard-library/monotonic-buffer-resource-class.md)||
|[pool_options – struktura](../standard-library/pool-options-structure.md)||
|[synchronized_pool_resource třídy](../standard-library/synchronized-pool-resource-class.md)||
|[unsynchronized_pool_resource třídy](../standard-library/unsynchronized-pool-resource-class.md)||

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
