---
title: allocator_newdel – třída
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_newdel
- allocators/stdext::allocator_newdel
- stdext::allocators::allocator_newdel
helpviewer_keywords:
- stdext::allocators [C++], allocator_newdel
- stdext::allocator_newdel
ms.assetid: 62666cd2-3afe-49f7-9dd1-9bbbb154da98
ms.openlocfilehash: d49a1596371e4a69873b826d3e756f263539d034
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448313"
---
# <a name="allocatornewdel-class"></a>allocator_newdel – třída

Implementuje Alokátor, který používá **operátor delete** k navrácení bloku paměti a **operátoru new** pro přidělení bloku paměti.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator_newdel;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Typ*|Typ prvků přidělených přidělováním.|

## <a name="remarks"></a>Poznámky

Makro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) předá tuto třídu jako parametr *Name* v následujícím příkazu:`ALLOCATOR_DECL(CACHE_FREELIST stdext::allocators::max_none), SYNC_DEFAULT, allocator_newdel);`

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> přidělování

**Obor názvů:** stdext

## <a name="see-also"></a>Viz také:

[\<allocators>](../standard-library/allocators-header.md)
