---
title: iterator – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xutility/std::iterator
dev_langs:
- C++
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a399fa8a9f8fc9a73d75605f31245e42a2154b7c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963625"
---
# <a name="iterator-struct"></a>iterator – struktura

Prázdná základní struktura používá k zajištění, že uživatelský iterátoru třídu správně funguje s `iterator_trait`s.

## <a name="syntax"></a>Syntaxe

```cpp
struct iterator {
   typedef Category iterator_category;
   typedef Type value_type;
   typedef Distance difference_type;
   typedef Distance distance_type;
   typedef Pointer pointer;
   typedef Reference reference;
   };
```

## <a name="remarks"></a>Poznámky

Struktura šablony slouží jako základní typ pro všechny iterátory. Definuje typy členů

- `iterator_category` (synonymum pro parametr šablony `Category`).

- `value_type` (synonymum pro parametr šablony `Type`).

- `difference_type` (synonymum pro parametr šablony `Distance`).

- `distance_type` (synonymum pro parametr šablony `Distance`)

- `pointer` (synonymum pro parametr šablony `Pointer`).

- `reference` (synonymum pro parametr šablony `Reference`).

Všimněte si, že `value_type` by neměl být konstantní typ i v případě `pointer` bodů v objektu **const** `Type` a odkaz označí objekt **const** `Type`.

## <a name="example"></a>Příklad

Zobrazit [iterator_traits –](../standard-library/iterator-traits-struct.md) příklad toho, jak deklarovat a použití typů v základní třídě iterátoru.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterátor >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[\<iterátor >](../standard-library/iterator.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
