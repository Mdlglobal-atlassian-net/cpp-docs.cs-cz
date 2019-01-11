---
title: Konstanty jazyka C s plovoucí desetinnou čárkou
ms.date: 11/04/2016
helpviewer_keywords:
- types [C], constants
- floating-point numbers, floating-point constants
- constants, floating-point
- floating-point constants
- floating-point constants, about floating-point constants
- double data type, floating-point constants
ms.assetid: e1bd9b44-d6ab-470c-93e5-07142c7a2062
ms.openlocfilehash: 2bde8ecdfa7e93160a86829c466ab9a78b71d48e
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220371"
---
# <a name="c-floating-point-constants"></a>Konstanty jazyka C s plovoucí desetinnou čárkou

"S plovoucí desetinnou čárkou konstanta" je desetinné číslo představující reálné číslo se znaménkem. Reprezentace reálné číslo se znaménkem obsahuje celočíselnou část desetinné části a exponent. Konstanty s plovoucí desetinnou čárkou použijte k reprezentaci hodnoty s plovoucí desetinnou čárkou, které se nedá změnit.

## <a name="syntax"></a>Syntaxe

*konstanta plovoucí desetinnou*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*desetinná konstanta* *exponent část*<sub>optimalizované</sub> *s plovoucí desetinnou čárkou přípona*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekvence číslic* *exponent část* *s plovoucí desetinnou čárkou přípona*<sub>optimalizované</sub>

*desetinná konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekvence číslic*<sub>optimalizované</sub> **.** *sekvence číslic*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekvence číslic*  **.**

*exponent část*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**elektronické** *přihlašování*<sub>optimalizované</sub> *sekvence číslic*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**elektronické** *přihlašování*<sub>optimalizované</sub> *sekvence číslic*

*znaménko*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**+ -**

*sekvence číslic*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*číslice*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekvence číslic* *číslice*

*číslo s plovoucí čárkou přípona*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**l f F L**

Můžete vynechat buď číslic od desetinné čárky (celočíselnou část hodnoty) nebo číslice za desetinnou čárkou (zlomkové části), ale ne obě možnosti současně. Můžete ponechat si desetinné čárky pouze v případě, že zahrnete exponent. Žádné prázdné znaky mohou oddělit číslic nebo znaků konstanty.

Následující příklady znázorňují některé formy konstanty s plovoucí desetinnou čárkou a výrazů:

```C
15.75
1.575E1   /* = 15.75   */
1575e-2   /* = 15.75   */
-2.5e-3   /* = -0.0025 */
25E-4     /* =  0.0025 */
```

Konstanty s plovoucí desetinnou čárkou jsou kladné, pokud jsou uvozená znakem minus (**-**). Znaménko minus v tomto případě je považován za unární operátor aritmetické negace. Konstanty s plovoucí desetinnou čárkou, mají typ `float`, `double`, nebo `long double`.

Konstanty s plovoucí desetinnou čárkou bez **f**, **F**, **l**, nebo **L** přípona nemá typ `double`. Pokud písmeno **f** nebo **F** je přípona, má typ konstanty `float`. Pokud příponou písmenem **l** nebo **L**, má typ `long double`. Příklad:

```C
10.0L  /* Has type long double  */
10.0F  /* Has type float        */
```

Všimněte si, že kompilátor Microsoft C interně představuje `long double` stejný jako typ `double`. Zobrazit [úložiště základních typů](../c-language/storage-of-basic-types.md) informace o typu `double`, `float`, a `long double`.

Vynechat celočíselnou část konstanty s plovoucí desetinnou čárkou, jak je znázorněno v následujícím příkladu. Číslo.75 může být vyjádřena v mnoha způsoby, včetně následujících:

```C
.0075e2
0.075e1
.075e1
75e-2
```

## <a name="see-also"></a>Viz také

[Konstanty jazyka C](../c-language/c-constants.md)
