---
title: Na základě Pointers (C) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- __based keyword [C]
- based pointers
- pointers, based
- based addressing
ms.assetid: b5446920-89e0-4e2f-91f3-1f2a769a08e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 79e515a3f108d0857d2f8860566e14ee0acdefe3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097572"
---
# <a name="based-pointers-c"></a>Základní ukazatelé (C)

**Specifické pro Microsoft**

[__based (referenční dokumentace jazyka C++)](../cpp/based-pointers-cpp.md)

Pro Microsoft 32bitové a 64bitové kompilátory jazyka C je 32bitová nebo 64bitová verze posun z 32bitové nebo 64bitové ukazatele na základní ukazatel. Na základě adresování je užitečné pro kontrolu nad části, kde jsou přidělené objekty výkonu, a tím zmenšit velikost spustitelný soubor a zvýšit rychlost provádění. Obecně je formulář pro určení ukazatele

> *typ* **__based (** *základní* **)** *deklarátorů*

"Podle ukazatel" varianta založené na adresování umožňuje specifikaci ukazatele jako základ. Ukazatel based, pak je posun do oddílu paměti začínající na začátku ukazatel, na které je založená. Ukazatele založené na adresách ukazatelů jsou jedinou formou `__based` – klíčové slovo platná ve 32bitových a 64bitových kompilacích. V takových kompilace jsou 32bitové nebo 64bitové posunutí z 32bitové nebo 64bitové base.

Jedním použitím ukazatelů na základě ukazatelů jsou trvalé identifikátory, které obsahují ukazatele. Propojený seznam, který se skládá z ukazatelů založených na ukazateli lze uložit na disk a následně jej lze znovu načíst na jiné místo v paměti, při současném zachování platnosti ukazatelů.

Následující příklad ukazuje ukazatel založených na ukazateli.

```C
void *vpBuffer;

struct llist_t
{
    void __based( vpBuffer ) *vpData;
    struct llist_t __based( vpBuffer ) *llNext;
};
```

Ukazateli `vpBuffer` je přiřazena adresa paměti, která je přidělena v programu později. Propojený seznam je přemístěn vzhledem k hodnotě `vpBuffer`.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)