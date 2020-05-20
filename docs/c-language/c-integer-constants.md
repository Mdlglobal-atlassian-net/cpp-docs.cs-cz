---
title: Konstanty typu Integer jazyka C
ms.date: 02/27/2018
helpviewer_keywords:
- integer constants
ms.assetid: fcf6b83c-2038-49ec-91ca-3d5ca1f83037
ms.openlocfilehash: 48561599896bb8a6f9ee159630ff15df6c0454be
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400516"
---
# <a name="c-integer-constants"></a>Konstanty typu Integer jazyka C

*Celočíselná konstanta* je desetinná čárka (Base 10), osmičková (základní 8) nebo hexadecimální (základní 16) číslo představující integrální hodnotu. Použijte celočíselné konstanty k vyjádření celočíselných hodnot, které nelze změnit.

## <a name="syntax"></a>Syntaxe

*celočíselná konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Volitelná možnost pro *celočíselnou příponu*<sub>opt</sub> typu *Decimal*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*osmičková* , *celočíselná přípona –*<sub>výslovný souhlas</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typ předpony*<sub>opt</sub> v *šestnáctkové soustavě konstanty*

*Desítková konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Nenulová číslice*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*desítková číslice s konstantou* *digit*

*osmičková konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0,8**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*osmičková-konstantní* *osmičková číslice*

*šestnáctková konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;šestnáctkové *číslo* *předpony* v šestnáctkové soustavě<br/>
&nbsp;&nbsp;&nbsp;&nbsp;šestnáctková *číslice* v *šestnáctkové soustavě*

*šestnáctková předpona*: jedna z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0x**  **0x**

*nenulová číslice*: jedna hodnota z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**

*osmičková číslice*: jedna z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7**

*šestnáctková číslice*: jedna z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**a b c d e f**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F**

*celočíselná přípona*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přípona* *dlouhé*<sub>přípony</sub> bez přípony<br/>
&nbsp;&nbsp;&nbsp;&nbsp;dlouhá *přípona bez přípony* – *dlouhá přípona*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přípona bez znaménka* *64-bit-integer-přípona*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přípona*<sub>opt</sub> *dlouhé přípony bez přípony*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*dlouhá* *unsigned-suffix*<sub>přípona</sub> bez přípony bez přípony<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*64-bitová celočíselná Přípona*

*přípona bez znaménka*: jedna z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**u U**

*Long-přípona*: jedna z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**l L**

*Long-Long-přípona*: jedna z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**vše**

*64-bitová celočíselná přípona*: jedna z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**I64 I64**

Přípony **I64** a **I64** jsou specifické pro společnost Microsoft.

Celočíselné konstanty jsou kladné, pokud nejsou předcházejí znaménkem mínus ( **-** ). Znaménko mínus je interpretováno jako unární aritmetický operátor negace. (Další informace o tomto operátoru naleznete v tématu [unární aritmetické operátory](../c-language/unary-arithmetic-operators.md) .)

Pokud celočíselná konstanta začíná **0x** nebo **0x**, je hexadecimální. Pokud začíná číslicí **0**, je osmičková. V opačném případě se předpokládá jako desetinné číslo.

Následující celočíselné konstanty jsou ekvivalentní:

```C
28
0x1C   /* = Hexadecimal representation for decimal 28 */
034    /* = Octal representation for decimal 28 */
```

Žádné prázdné znaky nemohou oddělovat číslice celočíselné konstanty. Tyto příklady ukazují některé platné desítkové, osmičkové a šestnáctkové konstanty.

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
