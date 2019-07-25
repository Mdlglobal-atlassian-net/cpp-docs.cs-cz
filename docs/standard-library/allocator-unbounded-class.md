---
title: allocator_unbounded – třída
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
ms.openlocfilehash: 38ecec3848808585ac0ed7cb1b076480a79f6d41
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448300"
---
# <a name="allocatorunbounded-class"></a>allocator_unbounded – třída

Popisuje objekt, který spravuje přidělování úložiště a uvolňuje pro objekty typu Type *pomocí mezipaměti* typu [cache_freelist](../standard-library/cache-freelist-class.md) s délkou spravovanou [max_unbounded](../standard-library/max-unbounded-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator_unbounded;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Typ*|Typ prvků přidělených přidělováním.|

## <a name="remarks"></a>Poznámky

Makro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) předá tuto třídu jako parametr *Name* v následujícím příkazu:`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> přidělování

**Obor názvů:** stdext

## <a name="see-also"></a>Viz také:

[\<allocators>](../standard-library/allocators-header.md)
