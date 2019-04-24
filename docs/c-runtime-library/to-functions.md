---
title: to – funkce
ms.date: 11/04/2016
apilocation:
- msvcr120.dll
- msvcr90.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- To
helpviewer_keywords:
- to functions
- string conversion, to different characters
- string conversion, case
- lowercase, converting strings
- uppercase, converting strings
- case, converting
- characters, converting
ms.assetid: f636a4c6-8c9f-4be2-baac-064f9dbae300
ms.openlocfilehash: 17d80507462b3eb0fdfb5d9e41da6162947bd3de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62304394"
---
# <a name="to-functions"></a>to – funkce

Každá z **k** funkce a její přidružené – makro, pokud existuje, převede jeden znak jinému znaku.

|||
|-|-|
|[__toascii](../c-runtime-library/reference/toascii-toascii.md)|[ToUpper _toupper –, towupper –](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|
|[tolower, _tolower, towlower](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)||

## <a name="remarks"></a>Poznámky

**k** funkce a makro převody jsou následující.

|Rutina|– Makro|Popis|
|-------------|-----------|-----------------|
|`__toascii`|`__toascii`|Převede `c` znak ASCII|
|`tolower`|`tolower`|Převede `c` na malá písmena v případě potřeby|
|`_tolower`|`_tolower`|Převede `c` na malá písmena|
|`towlower`|Žádné|Převede `c` na odpovídající širokého znaku malé písmeno|
|`toupper`|`toupper`|Převede `c` na velká písmena v případě potřeby|
|`_toupper`|`_toupper`|Převede `c` na velká písmena|
|`towupper`|Žádné|Převede c na odpovídající širokého znaku velké písmeno|

Používat funkce verze **k** rutin, které jsou také definovány jako makra, buď odeberte definice maker s `#undef` direktivy nebo nezahrnují CTYPE. H. Pokud použijete možnosti kompilátoru /Za, kompilátor používá verzi funkce `toupper` nebo `tolower`. Deklarace `toupper` a `tolower` funkce jsou v STDLIB. H.

`__toascii` Rutinní nastaví všechny, ale 7 bity nižšího řádu `c` na hodnotu 0, tak, aby převedená hodnota představuje znak ve znakové sadě ASCII. Pokud `c` již znaku ASCII, představuje `c` se nezmění.

`tolower` a `toupper` rutiny:

- Na kterých závisí `LC_CTYPE` kategorie aktuálního národního prostředí (`tolower` volání `isupper` a `toupper` volání `islower`).

- Převést `c` Pokud `c` představuje písmeno převést má správnou velikost písmen v aktuální národní prostředí a opačném případě existuje pro toto národní prostředí. V opačném případě `c` je beze změny.

`_tolower` a `_toupper` rutiny:

- Jsou nezávislé na národní prostředí a mnohem rychlejší verze `tolower` a **toupper.**

- Lze použít pouze tehdy, když **isascii – (**`c`**)** a buď **isupper (**`c`**)** nebo **islower (**`c`**)**, jsou nenulové.

- Pokud máte nedefinované výsledky `c` není písmeno ASCII správnou velikost písmen pro převod.

`towlower` a `towupper` funkce vrací převedený kopie `c` pouze v případě jsou splněny obě následující podmínky nenulovou hodnotu. V opačném případě `c` je beze změny.

- `c` je široký znak má správnou velikost písmen (to znamená, pro kterou `iswupper` nebo **iswlower –,** , je nenulové).

- Existuje široký znak odpovídající cílové případu (to znamená, pro kterou `iswlower` nebo **iswupper –,** , je nenulové).

## <a name="example"></a>Příklad

```
// crt_toupper.c
/* This program uses toupper and tolower to
 * analyze all characters between 0x0 and 0x7F. It also
 * applies _toupper and _tolower to any code in this
 * range for which these functions make sense.
 */

#include <ctype.h>
#include <string.h>

char msg[] = "Some of THESE letters are Capitals.";
char *p;

int main( void )
{
   printf( "%s\n", msg );

   /* Reverse case of message. */
   for( p = msg; p < msg + strlen( msg ); p++ )
   {
      if( islower( *p ) )
         putchar( _toupper( *p ) );
      else if( isupper( *p ) )
         putchar( _tolower( *p ) );
      else
         putchar( *p );
   }
}
```

```Output
Some of THESE letters are Capitals.
sOME OF these LETTERS ARE cAPITALS.
```

## <a name="see-also"></a>Viz také:

[Převod dat](../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../c-runtime-library/locale.md)<br/>
[is, isw – rutiny](../c-runtime-library/is-isw-routines.md)
