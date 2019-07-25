---
title: '&lt;memory_resource&gt;'
ms.date: 04/04/2019
f1_keywords:
- <memory_resource>
helpviewer_keywords:
- memory_resource header
ms.openlocfilehash: d4b25c6ee575191f1e17b0202d33298e2e9e67f0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451907"
---
# <a name="ltmemoryresourcegt"></a>&lt;memory_resource&gt;

Definuje třídu šablony kontejneru memory_resource a její podpůrné šablony.

## <a name="syntax"></a>Syntaxe

```cpp
#include <memory_resource>
```

## <a name="members"></a>Členové

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator!=](../standard-library/memory-resource-operators.md#op_neq)|Testuje, zda objekt memory_resource na levé straně operátoru není roven objektu memory_resource na pravé straně.|
|[operator==](../standard-library/memory-resource-operators.md#op_eq_eq)|Testuje, zda je objekt memory_resource na levé straně operátoru roven objektu memory_resource na pravé straně.|

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
|[memory_resource – třída](../standard-library/memory-resource-class.md)||
|[monotonic_buffer_resource – třída](../standard-library/monotonic-buffer-resource-class.md)||
|[pool_options – struktura](../standard-library/pool-options-structure.md)||
|[synchronized_pool_resource – třída](../standard-library/synchronized-pool-resource-class.md)||
|[unsynchronized_pool_resource – třída](../standard-library/unsynchronized-pool-resource-class.md)||

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
