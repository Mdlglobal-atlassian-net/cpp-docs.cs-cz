---
title: type_index – třída
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::type_index
helpviewer_keywords:
- type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
ms.openlocfilehash: b30c9719957b9ffc5f3ce17692eb90c1b266ae0f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447057"
---
# <a name="typeindex-class"></a>type_index – třída

Třída obaluje ukazatel na [třídu type_info](../cpp/type-info-class.md) , která pomáhá při indexování těmito objekty. `type_index`

Třída type_index {Public: type_index (const type_info & tinfo); const char * Name () const; size_t hash_code () const; bool operator = = (const type_info & Right) const, bool operator! = (const type_info & Right) const, bool operator < (const type_ info & Right) const; bool –\<operátor = (const type_info & Right) const; bool operátor > (const type_info & Right) const; bool operátor > = (const type_info & Right) const;};

Konstruktor se inicializuje `ptr` na `&tinfo`.

`name`Vrátí `ptr->name()`.

`hash_code`Vrátí`ptr->hash_code().`

`operator==`Vrátí `*ptr == right.ptr`.

`operator!=`Vrátí `!(*this == right)`.

`operator<`Vrátí `*ptr->before(*right.ptr)`.

`operator<=`Vrátí`!(right < *this).`

`operator>`Vrátí `right < *this`.

`operator>=`Vrátí `!(*this < right)`.

## <a name="see-also"></a>Viz také:

[Informace o typu běhového běhu](../cpp/run-time-type-information.md)\
[\<typeindex>](../standard-library/typeindex.md)
