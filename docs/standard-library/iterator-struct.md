---
title: iterator – struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
ms.openlocfilehash: 64c9be76cb92d818e40714dd141ded3a8cc17c8a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455624"
---
# <a name="iterator-struct"></a>iterator – struktura

Prázdná základní struktura se používá k zajištění toho, aby uživatelsky definovaná třída iterátoru správně `iterator_trait`fungovala s.

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

- `iterator_category`(synonymum pro parametr `Category`šablony).

- `value_type`(synonymum pro parametr `Type`šablony).

- `difference_type`(synonymum pro parametr `Distance`šablony).

- `distance_type`(synonymum pro parametr `Distance`šablony)

- `pointer`(synonymum pro parametr `Pointer`šablony).

- `reference`(synonymum pro parametr `Reference`šablony).

Všimněte si `value_type` , že by neměl být konstantní typ i `pointer` v případě, že body  `Type` na objektu const a reference určují objekt  `Type`typu const.

## <a name="example"></a>Příklad

Příklad, jak deklarovat a používat typy v základní třídě iterátoru, naleznete v tématu [iterator_traits](../standard-library/iterator-traits-struct.md) .

## <a name="requirements"></a>Požadavky

**Hlavička:** \<iterátor >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[\<iterátor >](../standard-library/iterator.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
