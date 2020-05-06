---
title: Zřetězení textového literálu
ms.date: 11/04/2016
helpviewer_keywords:
- concatenating strings
- strings [C++], concatenating
ms.assetid: 51486b1f-4b1e-4061-9add-1aa38c6cdb3c
ms.openlocfilehash: cdd9a7811635bf43cd76ecbc84d8ab364e7f9dab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157785"
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

Chcete-li vynutit nový řádek v rámci řetězcového literálu, zadejte řídicí sekvence nového řádku (**\n**) v místě v řetězci, kde má být řádek přerušen, následovně:

```
"Enter a number between 1 and 100\nOr press Return"
```

Protože řetězce mohou začínat na jakémkoli sloupci zdrojového kódu a dlouhé řetězce mohou pokračovat na jakémkoli sloupci následujícího řádku, umístěním řetězců lze vylepšit čitelnost zdrojového kódu. V obou případech není jejich reprezentace na obrazovce při výstupu ovlivněna. Příklad:

```
printf_s ( "This is the first half of the string, "
           "this is the second half ") ;
```

Pokud je každá část řetězce uzavřená v uvozovkách, jsou tyto části zřetězeny a na výstupu jsou jako jeden řetězec. K tomuto zřetězení dochází v závislosti na sekvenci událostí během kompilace určené pomocí [fází překladu](../preprocessor/phases-of-translation.md).

```
"This is the first half of the string, this is the second half"
```

Ukazatel na řetězec, inicializovaný jako dva jedinečné řetězcové literály oddělené pouze prázdným znakem, je uložen jako jeden řetězec (ukazatele jsou popsány v tématu [deklarace ukazatelů](../c-language/pointer-declarations.md)). Při správném odkazování je výsledek v následujícím příkladu stejný jako v předchozím příkladu:

```
char *string = "This is the first half of the string, "
               "this is the second half";

printf_s( "%s" , string ) ;
```

Ve fázi překladu 6 jsou vícebajtové znakové sekvence určené libovolnou sekvencí sousedních textových literálů nebo sousedních literálů širokých řetězců zřetězeny do jediné vícebajtové sekvence znaků. Proto nenavrhujte programy umožňující změnu textových literálů během provádění. Standard ANSI jazyka C určuje, že výsledek změny řetězce není definován.

## <a name="see-also"></a>Viz také

[Textové literály jazyka C](../c-language/c-string-literals.md)
