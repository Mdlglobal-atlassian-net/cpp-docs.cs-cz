---
title: Komentáře v jazyce C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- code comments, C code
- comments, documenting code
- comments, C code
- /* */ comment delimiters
- comments
ms.assetid: 0f5f2825-e673-49e7-8669-94e2f5294989
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2e91f2c4769483ce5d1a3926d52c7a48fdd2810
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314270"
---
# <a name="c-comments"></a>Komentáře v jazyce C

"Komentář" je posloupnost znaků začínající kombinací lomítka a hvězdičky (<strong>/\*</strong>), který je považován za jeden prázdný znak kompilátorem a je jinak ignorována. Komentář může obsahovat libovolnou kombinaci znaků znakové sady, včetně znaků nového řádku, s výjimkou oddělovače "konec komentáře" (<strong>\*/</strong>). Komentáře mohou zaujímat více než jeden řádek, ale nelze je vnořovat.

Komentáře se mohou vyskytovat kdekoliv, kde je povolen prázdný znak. Protože kompilátor považuje komentáře za jeden prázdný znak, nelze komentáře zadávat v tokenech. Kompilátor ignoruje znaky v komentáři.

Komentáře lze použít k dokumentaci kódu. Tento příklad je komentář, který kompilátor přijímá:

```C
/* Comments can contain keywords such as
   for and while without generating errors. */
```

Komentáře se mohou vyskytovat na stejném řádku, na kterém se vyskytuje příkaz kódu:

```C
printf( "Hello\n" );  /* Comments can go here */
```

Funkcím nebo modulům programu mohou předcházet popisné bloky komentáře:

```C
/* MATHERR.C illustrates writing an error routine
* for math functions.
*/
```

Protože nemohou komentáře nemohou vnořené komentáře, tento příklad způsobí chybu:

```C
/* Comment out this routine for testing

   /* Open file */
    fh = _open( "myfile.c", _O_RDONLY );
    .
    .
    .
*/
```

K této chybě dochází, protože kompilátor rozpozná první znak `*/` za slovy `Open file` jako konec komentáře. Pokusí se zpracovat zbývající text a po nalezení znaku `*/` mimo komentář vygeneruje chybu.

Ačkoli lze komentáře použít k deaktivaci určitých řádků kódu za účelem testování, jsou užitečnou alternativou pro tento úkol direktivy preprocesoru `#if` a `#endif` a podmíněné kompilace. Další informace najdete v tématu [direktivy preprocesoru](../preprocessor/preprocessor-directives.md) v *odkazu preprocesoru*.

**Specifické pro Microsoft**

Kompilátor společnosti Microsoft podporuje také Jednořádkové komentáře, které předchází dvě lomítka (__//__). Je-li program kompilován s možností /Za (standard ANSI), vygenerují tyto komentáře chyby. Tyto komentáře nemohou přesahovat na druhý řádek.

```C
// This is a valid comment
```

Komentáře začínající dvěma lomítky (__//__) jsou ukončeny následujícím znakem, který není předcházen řídicím znakem. V následujícím příkladu je znak nového řádku předcházen zpětným lomítkem (**\\**), vytváření "řídicí sekvence". Díky této řídicí sekvenci kompilátor považuje další řádek za součást předchozího řádku. (Další informace najdete v tématu [řídicí sekvence](../c-language/escape-sequences.md).)

```C
// my comment \
    i++;
```

Příkaz `i++;` je proto zakomentován.

Výchozí nastavení pro Microsoft C je, že jsou povolena rozšíření společnosti Microsoft. Chcete-li tato rozšíření zakázat, použijte možnost /Za.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Tokeny jazyka C](../c-language/c-tokens.md)
