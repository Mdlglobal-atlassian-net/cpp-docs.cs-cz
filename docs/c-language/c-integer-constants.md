---
title: Konstanty typu Integer jazyka C
ms.date: 02/27/2018
helpviewer_keywords:
- integer constants
ms.assetid: fcf6b83c-2038-49ec-91ca-3d5ca1f83037
ms.openlocfilehash: 4a3d6b945f3611b8e51029c0a5ec5dc77b2cbaa0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620217"
---
# <a name="c-integer-constants"></a>Konstanty typu Integer jazyka C

*Celočíselná konstanta* desetinné číslo (se základem 10), osmičkové (základní 8) nebo šestnáctkové (základní 16) číslo, které představuje celé číslo. Konstanty typu integer použijte k vyjádření celočíselných hodnot, která se nedá změnit.

## <a name="syntax"></a>Syntaxe

*celočíselná konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*desetinná konstanta* *číselnou příponou*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*osmičkové konstanty* *číselnou příponou*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*šestnáctkové konstanty* *číselnou příponou*<sub>optimalizované</sub><br/>

*desetinná konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nenulovou číslicí.*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*desetinná konstanta* *číslice*<br/>

*osmičkové konstanty*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*osmičkové konstanty* *uveden jako osmičková číslice*<br/>

*šestnáctkové konstanty*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-prefix* *hexadecimal-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*šestnáctkové konstanty* *šestnáctkové číslice*<br/>

*Předpona šestnáctkové*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0x**  **0X**<br/>

*nenulovou číslicí*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**<br/>

*uveden jako osmičková číslice*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7**<br/>

*šestnáctkové číslice*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**b c d e f**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F**<br/>

*integer-suffix*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-suffix*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long long-suffix*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *64 bit číselnou příponou*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Long-suffix* *unsigned-suffix*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Long long-suffix* *unsigned-suffix*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*64-bit-integer-suffix*<br/>

*unsigned-suffix*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**u U**<br/>

*Long-suffix*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**l L**<br/>

*Long long-suffix*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**ll, LL**<br/>

*64-bit číselnou příponou*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**I64 I64**<br/>

**I64** a **I64** přípony jsou specifické pro společnost Microsoft.

Celočíselné konstanty jsou kladné, pokud jsou uvozená znakem minus (**-**). Znaménko minus je interpretován jako operátor unární aritmetické negace. (Viz [unární aritmetické operátory](../c-language/unary-arithmetic-operators.md) informace o tomto operátoru.)

Pokud celočíselná konstanta začíná **0 x** nebo **0 X**, je šestnáctková. Pokud začíná číslice **0**, je osmičkové soustavě. V opačném případě se předpokládá být desítkové.

Následující konstanty typu integer jsou ekvivalentní:

```C
28
0x1C   /* = Hexadecimal representation for decimal 28 */
034    /* = Octal representation for decimal 28 */
```

Žádné prázdné znaky mohou oddělit číslic celočíselná konstanta. Tyto příklady ukazují některé platné desetinné, osmičkovým a šestnáctkovým konstantám.

```C
    /* Decimal Constants */
    int                 dec_int    = 28;
    unsigned            dec_uint   = 4000000024u;
    long                dec_long   = 2000000022l;
    unsigned long       dec_ulong  = 4000000000ul;
    long long           dec_llong  = 9000000000LL;
    unsigned long long  dec_ullong = 900000000001ull;
    __int64             dec_i64    = 9000000000002I64;
    unsigned __int64    dec_ui64   = 90000000000004ui64;

    /* Octal Constants */
    int                 oct_int    = 024;
    unsigned            oct_uint   = 04000000024u;
    long                oct_long   = 02000000022l;
    unsigned long       oct_ulong  = 04000000000UL;
    long long           oct_llong  = 044000000000000ll;
    unsigned long long  oct_ullong = 044400000000000001Ull;
    __int64             oct_i64    = 04444000000000000002i64;
    unsigned __int64    oct_ui64   = 04444000000000000004uI64;

    /* Hexadecimal Constants */
    int                 hex_int    = 0x2a;
    unsigned            hex_uint   = 0XA0000024u;
    long                hex_long   = 0x20000022l;
    unsigned long       hex_ulong  = 0XA0000021uL;
    long long           hex_llong  = 0x8a000000000000ll;
    unsigned long long  hex_ullong = 0x8A40000000000010uLL;
    __int64             hex_i64    = 0x4a44000000000020I64;
    unsigned __int64    hex_ui64   = 0x8a44000000000040Ui64;
```

## <a name="see-also"></a>Viz také:

[Konstanty jazyka C](../c-language/c-constants.md)<br/>
