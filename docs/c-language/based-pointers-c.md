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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327428"
---
# <a name="based-pointers-c"></a>Základní ukazatelé (C)

**Specifické pro Microsoft**

[__based (Referenční dokumentace jazyka C++)](../cpp/based-pointers-cpp.md)

V případě kompilátorů jazyka C pro Microsoft 32 a 64 64 32 je ukazatel na základě verze v 32 nebo v základní části ukazatele s neplatným. Základní adresování je užitečné pro uplatnění kontroly nad oddíly, kde jsou objekty přidělené, a tím zmenšuje velikost spustitelného souboru a zvyšuje rychlost spuštění. Obecně platí, že formulář pro určení ukazatele based je

> *typ* **__based (** *základní* **)** *deklarátor*

"Založený na" variantě vycházejícího adresování umožňuje specifikace ukazatele jako základu. Ukazatel na základě, pak je posun do oddílu paměti začínající na začátku ukazatele, na kterém je založena. Ukazatele založené na adresách ukazatelů jsou jedinou formou `__based` klíčového slova platným v 32 bitových a 64 bitových kompilacích. V takových kompilacích jsou 32 nebo 64 bity z 32-bit 64 nebo z 16bitové základny.

Jedním použitím ukazatelů na základě ukazatelů jsou trvalé identifikátory, které obsahují ukazatele. Propojený seznam, který se skládá z ukazatelů založených na ukazateli lze uložit na disk a následně jej lze znovu načíst na jiné místo v paměti, při současném zachování platnosti ukazatelů.

Následující příklad ukazuje ukazatel na základě ukazatele.

```C
void *vpBuffer;

struct llist_t
{
    void __based( vpBuffer ) *vpData;
    struct llist_t __based( vpBuffer ) *llNext;
};
```

Ukazateli `vpBuffer` je přiřazena adresa paměti, která je přidělena v programu později. Propojený seznam je přemístěn vzhledem k hodnotě `vpBuffer`.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)
