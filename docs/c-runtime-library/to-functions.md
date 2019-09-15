---
title: to – funkce
ms.date: 11/04/2016
api_location:
- msvcr120.dll
- msvcr90.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: f7a898d70e506ed4707ea718faa0ed618682c2c7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944812"
---
# <a name="to-functions"></a>to – funkce

Každý z funkcí a přidruženého makra, **Pokud je,** převede jeden znak na jiný znak.

|||
|-|-|
|[__toascii](../c-runtime-library/reference/toascii-toascii.md)|[ToUpper, _toupper, towupper](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|
|[ToLower, _tolower, towlower](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)||

## <a name="remarks"></a>Poznámky

Na **funkce a** převody maker jsou následující.

|Rutina|– Makro|Popis|
|-------------|-----------|-----------------|
|`__toascii`|`__toascii`|Převede `c` na znak ASCII.|
|`tolower`|`tolower`|V `c` případě potřeby převede na malá písmena.|
|`_tolower`|`_tolower`|Převede `c` na malá písmena.|
|`towlower`|Žádné|Převede `c` na odpovídající malé písmeno s velkým znakem.|
|`toupper`|`toupper`|V `c` případě potřeby převede na velká písmena|
|`_toupper`|`_toupper`|Převede `c` na velká písmena.|
|`towupper`|Žádné|Převede jazyk c na odpovídající velké písmeno.|

Chcete **-li použít verze funkce rutiny** , které jsou také definovány jako makra, buď odeberte definice `#undef` maker direktivy nebo nezahrnujte CType. Y. Použijete-li možnost kompilátoru/za, kompilátor použije verzi `toupper` funkce nebo. `tolower` Deklarace funkcí `tolower` a jsou v Stdlib. `toupper` Y.

Rutina nastaví všechny s výjimkou méně než 7 `c` bitů na hodnotu 0, aby převedená hodnota představovala znak v sadě znaků ASCII. `__toascii` Pokud `c` již představuje znak ASCII, `c` je beze změny.

Rutiny `toupper`a: `tolower`

- Jsou závislé `LC_CTYPE` na kategorii aktuálního národního prostředí ( `isupper` `tolower` volání a `toupper` volání `islower`).

- Převést `c` , `c` pokud představuje konvertibilní písmena odpovídajícího případu v aktuálním národním prostředí a pro toto národní prostředí existuje opačný případ. V opačném případě se nemění. `c`

Rutiny `_toupper`a: `_tolower`

- Je nezávislý na národním prostředí, mnohem rychlejší verze `tolower` a **ToUpper.**

- Lze ji použít pouze v případě, že je nastavena hodnota "- **ASCII (** `c` **)** a" **Upper "(** `c` **) nebo"** **Lower "(** `c` **)** , jsou nenulové.

- Mít nedefinované výsledky, `c` Pokud se nejedná o písmeno ASCII příslušného případu pro převod.

Funkce `towlower` a `towupper` vracejípřevedenoukopiiifapouzevpřípadě,žeoběnásledujícípodmínky`c` jsou nenulové. V opačném případě se nemění. `c`

- `c`je velký znak vhodného případu (tj., pro který `iswupper` nebo **iswlower,** v uvedeném pořadí není nula).

- K dispozici je odpovídající velký znak cílového případu (tj., pro který `iswlower` nebo **iswupper,** v uvedeném pořadí není nula).

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
