---
title: allocator_chunklist – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::allocator_chunklist
- allocators/stdext::allocators::allocator_chunklist
dev_langs:
- C++
helpviewer_keywords:
- stdext::allocator_chunklist
- stdext::allocators [C++], allocator_chunklist
ms.assetid: ea72ed0a-dfdb-4c8b-8096-e4baf567b80f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20e601608b1a6b0f076040c10e027f7dc78db17a
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955355"
---
# <a name="allocatorchunklist-class"></a>allocator_chunklist – třída

Popisuje objekt, který spravuje rozdělení úložiště a uvolnění objektů použití mezipaměti typu [cache_chunklist –](../standard-library/cache-chunklist-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator_chunklist;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Typ*|Typ prvků přidělaná přidělujícího modulu.|

## <a name="remarks"></a>Poznámky

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) – makro předá tuto třídu jako *název* parametr v následujícím příkazu: `ALLOCATOR_DECL(CACHE_CHUNKLIST, SYNC_DEFAULT, allocator_chunklist);`

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátorů >

**Namespace:** stdext

## <a name="see-also"></a>Viz také:

[\<alokátory: >](../standard-library/allocators-header.md)<br/>
