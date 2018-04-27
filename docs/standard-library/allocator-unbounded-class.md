---
title: allocator_unbounded – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
dev_langs:
- C++
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9dbc7fff1d75e683ee36042e852ced68e82ec9dc
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="allocatorunbounded-class"></a>allocator_unbounded – třída

Popisuje objekt, který spravuje přidělení úložiště a uvolnění objektů typu `Type` použití mezipaměti typu [cache_freelist –](../standard-library/cache-freelist-class.md) s délkou spravuje [max_unbounded](../standard-library/max-unbounded-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator_unbounded;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`Type`|Typ elementů přidělené pomocí přidělujícího modulu.|

## <a name="remarks"></a>Poznámky

[Allocator_decl –](../standard-library/allocators-functions.md#allocator_decl) makro předá tuto třídu jako `name` parametr v následující příkaz: `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátorů >

**Namespace:** stdext –

## <a name="see-also"></a>Viz také

[\<alokátorů >](../standard-library/allocators-header.md)<br/>
