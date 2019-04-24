---
title: iterator – struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
ms.openlocfilehash: 1dd62a6141e690d3bd4dcad69aa107c126a0f386
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224100"
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

[\<iterator>](../standard-library/iterator.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
