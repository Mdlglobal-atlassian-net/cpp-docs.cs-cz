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
ms.openlocfilehash: df8f59088cd402503fe31f768557e3ed936b31ec
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301688"
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
|`tolower`|`tolower`|V případě potřeby převede `c` na malá písmena.|
|`_tolower`|`_tolower`|Převede `c` na malá písmena.|
|`towlower`|Žádné|Převede `c` na odpovídající malé písmeno s velkým znakem.|
|`toupper`|`toupper`|V případě potřeby převede `c` na velká písmena.|
|`_toupper`|`_toupper`|Převede `c` na velká písmena.|
|`towupper`|Žádné|Převede jazyk c na odpovídající velké písmeno.|

Chcete **-li použít verze funkce rutiny** , které jsou také definovány jako makra, buď odeberte definice makra pomocí direktiv `#undef` nebo nezahrnovat CType. Y. Použijete-li možnost kompilátoru/za, kompilátor použije verzi funkce `toupper` nebo `tolower`. Deklarace `toupper` a `tolower` funkcí jsou v STDLIB. Y.

Rutina `__toascii` nastaví všechny kromě dolních 7 bitů `c` na hodnotu 0, aby převedená hodnota představovala znak ve znakové sadě ASCII. Pokud `c` již představuje znak ASCII, `c` je beze změny.

Rutiny `tolower` a `toupper`:

- Jsou závislé na kategorii `LC_CTYPE` aktuálního národního prostředí (`tolower` volá `isupper` a `toupper` volání `islower`).

- Převede `c`, pokud `c` představuje konvertibilní znak z příslušného případu v aktuálním národním prostředí a pro toto národní prostředí existuje opačný případ. V opačném případě `c` nezměněný.

Rutiny `_tolower` a `_toupper`:

- Je nezávislý na národním prostředí, mnohem rychlejší verze `tolower` a **ToUpper.**

- Dá se použít jenom v případě, že je v režimu- **ASCII (** `c` **)** a buď **Upper (** `c` **)** nebo **Lower (** `c` **)** , v uvedeném pořadí nenulová hodnota.

- Mít nedefinované výsledky, pokud `c` není znak ASCII pro příslušný případ pro převod.

Funkce `towlower` a `towupper` vrací převedenou kopii `c` pouze v případě, že obě následující podmínky jsou nenulové. V opačném případě `c` nezměněný.

- `c` je velký znak vhodného případu (to znamená, že `iswupper` nebo **iswlower,** v uvedeném pořadí, není nula).

- K dispozici je odpovídající velký znak cílového případu (to znamená, pro který `iswlower` nebo **iswupper,** v uvedeném pořadí, není nula).

## <a name="example"></a>Příklad

```c
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
