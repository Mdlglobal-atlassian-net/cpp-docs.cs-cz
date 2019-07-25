---
title: allocator_variable_size – třída
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_variable_size
- allocators/stdext::allocators::allocator_variable_size
- stdext::allocators::allocator_variable_size
helpviewer_keywords:
- stdext::allocator_variable_size
- stdext::allocators [C++], allocator_variable_size
ms.assetid: c3aa4105-ae45-4385-bbbe-9f23060478cb
ms.openlocfilehash: bf243089ee8f4e26930e183b007a108e38f444e3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458159"
---
# <a name="allocatorvariablesize-class"></a>allocator_variable_size – třída

Popisuje objekt, který spravuje přidělování úložiště a uvolňuje pro objekty typu Type *pomocí mezipaměti* typu [cache_freelist](../standard-library/cache-freelist-class.md) s délkou spravovanou [max_variable_size](../standard-library/max-variable-size-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator_variable_size;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Typ*|Typ prvků přidělených přidělováním.|

## <a name="remarks"></a>Poznámky

Makro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) předá tuto třídu jako parametr *Name* v následujícím příkazu:`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_variable_size), SYNC_DEFAULT, allocator_variable_size);`

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> přidělování

**Obor názvů:** stdext

## <a name="see-also"></a>Viz také:

[\<allocators>](../standard-library/allocators-header.md)
