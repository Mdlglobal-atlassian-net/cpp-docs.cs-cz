---
title: type_index – třída
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::type_index
helpviewer_keywords:
- type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
ms.openlocfilehash: 8807a041ab1c6ef47a9c3c12dac2688f121f6cfa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278959"
---
# <a name="typeindex-class"></a>type_index – třída

`type_index` Třídy zabalí ukazatel na [type_info – třída](../cpp/type-info-class.md) pomáhat při indexování tyto objekty.

type_index – třída {public: type_index – (const type_info & tinfo); const char *name() const, size_t hash_code() const, bool – operátor == (const type_info & rava) const; bool – operátor! = (const type_info & pravé) const; <(const type_ bool – operátor informace o & rava) const; BOOL – operátor\<= (const type_info & pravé) const; bool – operátor > (const type_info & rava) const; bool – operátor > = (const type_info & pravé) const;};

Konstruktor inicializuje `ptr` k `&tinfo`.

`name` Vrátí `ptr->name()`.

`hash_code` Vrátí `ptr->hash_code().`

`operator==` Vrátí `*ptr == right.ptr`.

`operator!=` Vrátí `!(*this == right)`.

`operator<` Vrátí `*ptr->before(*right.ptr)`.

`operator<=` Vrátí `!(right < *this).`

`operator>` Vrátí `right < *this`.

`operator>=` Vrátí `!(*this < right)`.

## <a name="see-also"></a>Viz také:

[Informace o typu modulu runtime](../cpp/run-time-type-information.md)<br/>
[\<typeindex>](../standard-library/typeindex.md)<br/>
