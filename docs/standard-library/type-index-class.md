---
title: type_index – třída
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::type_index
helpviewer_keywords:
- type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
ms.openlocfilehash: 8807a041ab1c6ef47a9c3c12dac2688f121f6cfa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650488"
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
[\<typeindex >](../standard-library/typeindex.md)<br/>
