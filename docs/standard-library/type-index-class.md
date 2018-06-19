---
title: type_index – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- typeindex/std::type_index
dev_langs:
- C++
helpviewer_keywords:
- type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e301b8d47c1a054a5b80bff105950d876d90b047
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853993"
---
# <a name="typeindex-class"></a>type_index – třída

`type_index` Třída zabalí ukazatel na [type_info – třída](../cpp/type-info-class.md) pomoct indexování tyto objekty.

type_index – třída {veřejné: type_index (const type_info & tinfo); const char *name() const; size_t – hash_code() const; bool – operátor == (const type_info & doprava) const; bool – operátor! = (const type_info & doprava) const; <(const type_ bool – operátor informace o & doprava) const; BOOL – operátor\<= (const type_info & doprava) const; bool – operátor > (const type_info & doprava) const; bool – operátor > = (const type_info & doprava) const;};

Konstruktor inicializuje `ptr` k `&tinfo`.

`name` Vrátí `ptr->name()`.

`hash_code` Vrátí `ptr->hash_code().`

`operator==` Vrátí `*ptr == right.ptr`.

`operator!=` Vrátí `!(*this == right)`.

`operator<` Vrátí `*ptr->before(*right.ptr)`.

`operator<=` Vrátí `!(right < *this).`

`operator>` Vrátí `right < *this`.

`operator>=` Vrátí `!(*this < right)`.

## <a name="see-also"></a>Viz také

[Informace o typu modulu runtime](../cpp/run-time-type-information.md)<br/>
[\<typeindex >](../standard-library/typeindex.md)<br/>
