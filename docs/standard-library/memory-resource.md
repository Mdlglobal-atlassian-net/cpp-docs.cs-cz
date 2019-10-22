---
title: '&lt;memory_resource &gt;'
ms.date: 04/04/2019
f1_keywords:
- <memory_resource>
helpviewer_keywords:
- memory_resource header
ms.openlocfilehash: 752396bb06b292ce29b7c6cd292287955b6066a7
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687715"
---
# <a name="ltmemory_resourcegt"></a>&lt;memory_resource &gt;

Definuje šablonu třídy kontejneru memory_resource a její podpůrné šablony.

## <a name="syntax"></a>Syntaxe

```cpp
#include <memory_resource>
```

## <a name="members"></a>Členové

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator!=](../standard-library/memory-resource-operators.md#op_neq)|Testuje, zda objekt memory_resource na levé straně operátoru není roven objektu memory_resource na pravé straně.|
|[operator = = – operátor](../standard-library/memory-resource-operators.md#op_eq_eq)|Testuje, zda je objekt memory_resource na levé straně operátoru roven objektu memory_resource na pravé straně.|

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

@No__t_1 [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
