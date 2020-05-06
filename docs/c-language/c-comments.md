---
title: Komentáře v jazyce C
ms.date: 06/25/2018
helpviewer_keywords:
- code comments, C code
- comments, documenting code
- comments, C code
- /* */ comment delimiters
- comments
ms.assetid: 0f5f2825-e673-49e7-8669-94e2f5294989
ms.openlocfilehash: fd2c08855bcc3ef3b4068f3841ce177d8162ff5b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326284"
---
# <a name="c-comments"></a>Komentáře v jazyce C

"Comment" je posloupnost znaků začínající kombinací lomítka a hvězdičky (<strong>/</strong>), která je považována za jeden prázdný znak kompilátorem a je jinak ignorována. Komentář může obsahovat libovolnou kombinaci znaků ze sady reprezentující znak, včetně znaků nového řádku, ale bez oddělovače "koncový komentář" (<strong>\*</strong>). Komentáře mohou zaujímat více než jeden řádek, ale nelze je vnořovat.

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

Ačkoli lze komentáře použít k deaktivaci určitých řádků kódu za účelem testování, jsou užitečnou alternativou pro tento úkol direktivy preprocesoru `#if` a `#endif` a podmíněné kompilace. Další informace naleznete v tématu [direktivy preprocesoru](../preprocessor/preprocessor-directives.md) v *odkazu preprocesoru*.

**Specifické pro Microsoft**

Kompilátor společnosti Microsoft také podporuje Jednořádkový komentář, před kterým jsou vložena dvě lomítka (__//__). Je-li program kompilován s možností /Za (standard ANSI), vygenerují tyto komentáře chyby. Tyto komentáře nemohou přesahovat na druhý řádek.

```C
// This is a valid comment
```

Komentáře začínající dvěma lomítky (__//__) jsou ukončeny dalším znakem nového řádku, který nepředchází řídicí znak. V dalším příkladu před znakem nového řádku je zpětné lomítko (**\\**), které vytváří "řídicí sekvence". Díky této řídicí sekvenci kompilátor považuje další řádek za součást předchozího řádku. (Další informace najdete v tématu [řídicí sekvence](../c-language/escape-sequences.md).)

```C
// my comment \
    i++;
```

Příkaz `i++;` je proto zakomentován.

Výchozí hodnota pro Microsoft C znamená, že jsou rozšíření společnosti Microsoft povolena. Chcete-li tato rozšíření zakázat, použijte možnost /Za.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Tokeny jazyka C](../c-language/c-tokens.md)
