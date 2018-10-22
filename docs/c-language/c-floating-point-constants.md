---
title: Konstanty jazyka C s plovoucí desetinnou čárkou | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- types [C], constants
- floating-point numbers, floating-point constants
- constants, floating-point
- floating-point constants
- floating-point constants, about floating-point constants
- double data type, floating-point constants
ms.assetid: e1bd9b44-d6ab-470c-93e5-07142c7a2062
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23b5db965c8b4e29e8d25bad658189e7b37fc929
ms.sourcegitcommit: f9d9db80a8f13eae2c41337b974e1298109e33c5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2018
ms.locfileid: "49640763"
---
# <a name="c-floating-point-constants"></a>Konstanty jazyka C s plovoucí desetinnou čárkou

"S plovoucí desetinnou čárkou konstanta" je desetinné číslo představující reálné číslo se znaménkem. Reprezentace reálné číslo se znaménkem obsahuje celočíselnou část desetinné části a exponent. Konstanty s plovoucí desetinnou čárkou použijte k reprezentaci hodnoty s plovoucí desetinnou čárkou, které se nedá změnit.

## <a name="syntax"></a>Syntaxe

*konstanta plovoucí desetinnou*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*desetinná konstanta* *exponent část*<sub>optimalizované</sub> *s plovoucí desetinnou čárkou přípona*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekvence číslic* *exponent část* *s plovoucí desetinnou čárkou přípona*<sub>optimalizované</sub>

*desetinná konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekvence číslic*<sub>optimalizované</sub> **.** *sekvence číslic*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekvence číslic***.**

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

```
15.75
1.575E1   /* = 15.75   */
1575e-2   /* = 15.75   */
-2.5e-3   /* = -0.0025 */
25E-4     /* =  0.0025 */
```

Konstanty s plovoucí desetinnou čárkou jsou kladné, pokud jsou uvozená znakem minus (**-**). Znaménko minus v tomto případě je považován za unární operátor aritmetické negace. Konstanty s plovoucí desetinnou čárkou, mají typ `float`, `double`, nebo `long double`.

Konstanty s plovoucí desetinnou čárkou bez **f**, **F**, **l**, nebo **L** přípona nemá typ `double`. Pokud písmeno **f** nebo **F** je přípona, má typ konstanty `float`. Pokud příponou písmenem **l** nebo **L**, má typ `long double`. Příklad:

```
100L  /* Has type long double  */
100F  /* Has type float        */
```

Všimněte si, že kompilátor Microsoft C interně představuje `long double` stejný jako typ `double`. Zobrazit [úložiště základních typů](../c-language/storage-of-basic-types.md) informace o typu `double`, `float`, a `long double`.

Vynechat celočíselnou část konstanty s plovoucí desetinnou čárkou, jak je znázorněno v následujícím příkladu. Číslo.75 může být vyjádřena v mnoha způsoby, včetně následujících:

```
.0075e2
0.075e1
.075e1
75e-2
```

## <a name="see-also"></a>Viz také

[Konstanty jazyka C](../c-language/c-constants.md)
