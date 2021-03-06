---
title: allocator_chunklist – třída
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_chunklist
- allocators/stdext::allocators::allocator_chunklist
helpviewer_keywords:
- stdext::allocator_chunklist
- stdext::allocators [C++], allocator_chunklist
ms.assetid: ea72ed0a-dfdb-4c8b-8096-e4baf567b80f
ms.openlocfilehash: 46ae9c613b66e00658f09ad10f33b721c6948ff7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456429"
---
# <a name="allocatorchunklist-class"></a>allocator_chunklist – třída

Popisuje objekt, který spravuje přidělování úložiště a uvolňuje pro objekty pomocí mezipaměti typu [cache_chunklist](../standard-library/cache-chunklist-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator_chunklist;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Typ*|Typ prvků přidělených přidělováním.|

## <a name="remarks"></a>Poznámky

Makro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) předá tuto třídu jako parametr *Name* v následujícím příkazu:`ALLOCATOR_DECL(CACHE_CHUNKLIST, SYNC_DEFAULT, allocator_chunklist);`

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> přidělování

**Obor názvů:** stdext

## <a name="see-also"></a>Viz také:

[\<allocators>](../standard-library/allocators-header.md)
