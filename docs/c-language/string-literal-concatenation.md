---
title: Literál zřetězení řetězců | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- concatenating strings
- strings [C++], concatenating
ms.assetid: 51486b1f-4b1e-4061-9add-1aa38c6cdb3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a0d960a766c14b1e05dab461087669c0d44627d9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090073"
---
# <a name="string-literal-concatenation"></a>Zřetězení textového literálu

Chcete-li vytvořit textové literály, které zabírají více než jeden řádek, lze dva řetězce zřetězit. Chcete-li to provést, zadejte zpětné lomítko a poté stiskněte klávesu RETURN. Zpětné lomítko způsobí, že kompilátor bude ignorovat následující znak nového řádku. Například textový literál

```
"Long strings can be bro\
ken into two or more pieces."
```

je stejný jako řetězec

```
"Long strings can be broken into two or more pieces."
```

Zřetězení řetězců lze použít kdekoli tam, kde jste dříve použili zpětné lomítko následované znakem nového řádku pro zadání řetězců delších než jeden řádek.

Chcete-li vynutit nový řádek v rámci řetězce literálu, zadejte řídicí sekvenci nového řádku (**\n**) na místě v řetězci, kde chcete řádek rozdělit následujícím způsobem:

```
"Enter a number between 1 and 100\nOr press Return"
```

Protože řetězce mohou začínat na jakémkoli sloupci zdrojového kódu a dlouhé řetězce mohou pokračovat na jakémkoli sloupci následujícího řádku, umístěním řetězců lze vylepšit čitelnost zdrojového kódu. V obou případech není jejich reprezentace na obrazovce při výstupu ovlivněna. Příklad:

```
printf_s ( "This is the first half of the string, "
           "this is the second half ") ;
```

Pokud je každá část řetězce uzavřená v uvozovkách, jsou tyto části zřetězeny a na výstupu jsou jako jeden řetězec. K tomuto zřetězení dochází podle pořadí událostí během kompilace určené [fází překladu](../preprocessor/phases-of-translation.md).

```
"This is the first half of the string, this is the second half"
```

Ukazatel na řetězec, inicializován jako dva různé textové literály oddělené pouze prázdným znakem, je uložen jako jeden řetězec (ukazatele jsou uvedeny v [deklarace ukazatelů](../c-language/pointer-declarations.md)). Při správném odkazování je výsledek v následujícím příkladu stejný jako v předchozím příkladu:

```
char *string = "This is the first half of the string, "
               "this is the second half";

printf_s( "%s" , string ) ;
```

Ve fázi překladu 6 jsou vícebajtové znakové sekvence určené libovolnou sekvencí sousedních textových literálů nebo sousedních literálů širokých řetězců zřetězeny do jediné vícebajtové sekvence znaků. Proto nenavrhujte programy umožňující změnu textových literálů během provádění. Standard ANSI jazyka C určuje, že výsledek změny řetězce není definován.

## <a name="see-also"></a>Viz také

[Textové literály jazyka C](../c-language/c-string-literals.md)