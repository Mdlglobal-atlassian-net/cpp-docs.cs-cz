---
title: Základní ukazatelé (C)
ms.date: 11/04/2016
helpviewer_keywords:
- __based keyword [C]
- based pointers
- pointers, based
- based addressing
ms.assetid: b5446920-89e0-4e2f-91f3-1f2a769a08e8
ms.openlocfilehash: e5d8c529adfb92c9db1fdcc5a38f688853606d5d
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150776"
---
# <a name="based-pointers-c"></a>Základní ukazatelé (C)

**Microsoft Specific**

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

## <a name="see-also"></a>Viz také:

[Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)
