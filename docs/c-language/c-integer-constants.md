---
title: Konstanty typu Integer jazyka C | Microsoft Docs
ms.custom: ''
ms.date: 02/27/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integer constants
ms.assetid: fcf6b83c-2038-49ec-91ca-3d5ca1f83037
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eef5ba48d28b898ffc624d5790b0f414a8c112c3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389751"
---
# <a name="c-integer-constants"></a>Konstanty typu Integer jazyka C

*Celočíselná konstanta* desetinné číslo (se základem 10), osmičkové (základ 8), nebo je číslo šestnáctkové (základ 16), které představuje celočíselné hodnoty. Konstanty typu integer znázornit celočíselné hodnoty, které nelze změnit.

## <a name="syntax"></a>Syntaxe

*celočíselná konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Decimal – konstanta* *celé číslo příponu*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*osmičkové konstanta* *celé číslo příponu*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimální konstanta* *celé číslo příponu*<sub>opt</sub><br/>

*Decimal – konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nenulové hodnoty číslice*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Decimal – konstanta* *číslice*<br/>

*osmičkové konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*osmičkové konstanta* *osmičková číslice*<br/>

*hexadecimální konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-prefix* *hexadecimal-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimální konstanta* *šestnáctková číslice*<br/>

*hexadecimální předponu*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0x**  **0X**<br/>

*nenulové hodnoty v řádu*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**<br/>

*osmičková číslice*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7**<br/>

*hexadecimální číslice*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**b c d e f**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F**<br/>

*integer-suffix*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nepodepsané příponu* *dlouho příponu*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nepodepsané příponu* *dlouho. dlouho příponu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nepodepsané příponu* *64-bit-celé číslo příponu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Long příponu* *nepodepsané příponu*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Long long – přípona* *nepodepsané příponu*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*64-bit-integer-suffix*<br/>

*nepodepsané příponu*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**u U**<br/>

*Long příponu*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**l L**<br/>

*Long long – přípona*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Le le**<br/>

*64-bit-celé číslo přípona*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**I64 I64**<br/>

**I64** a **I64** přípony jsou specifické pro společnost Microsoft.

Konstanty typu Integer jsou kladné, pokud jsou sebou znaménkem minus (**-**). Mínus interpretována jako operátor unární aritmetické negace. (Viz [unární aritmetické operátory](../c-language/unary-arithmetic-operators.md) informace o tento operátor.)

Pokud začíná celočíselná konstanta **0 x** nebo **0 X**, je hexadecimální. Pokud začíná číslice **0**, je osmičková. Jinak se předpokládá, být decimal.

Následující konstanty typu integer jsou ekvivalentní:

```C
28
0x1C   /* = Hexadecimal representation for decimal 28 */
034    /* = Octal representation for decimal 28 */
```

Bez prázdných znaků můžete oddělit číslice celočíselná konstanta. Tyto příklady ukazují některé platné desetinné, osmičkových a šestnáctkových konstanty.

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

## <a name="see-also"></a>Viz také

[Konstanty jazyka C](../c-language/c-constants.md)<br/>
