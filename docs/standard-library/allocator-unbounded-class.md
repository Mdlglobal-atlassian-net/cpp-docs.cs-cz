---
title: allocator_unbounded – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
dev_langs:
- C++
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 321737f62d0e2506ef6582f80bed7f398ad5977b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959902"
---
# <a name="allocatorunbounded-class"></a>allocator_unbounded – třída

Popisuje objekt, který spravuje rozdělení úložiště a uvolnění pro objekt typu *typ* použití mezipaměti typu [cache_freelist –](../standard-library/cache-freelist-class.md) s délkou spravuje [max_unbounded –](../standard-library/max-unbounded-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator_unbounded;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Typ*|Typ prvků přidělaná přidělujícího modulu.|

## <a name="remarks"></a>Poznámky

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) – makro předá tuto třídu jako *název* parametr v následujícím příkazu: `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátorů >

**Namespace:** stdext

## <a name="see-also"></a>Viz také:

[\<alokátory: >](../standard-library/allocators-header.md)<br/>
