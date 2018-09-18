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
ms.openlocfilehash: e4ceed8fa38ae2b6801fa13c65e54f1cd1cc711d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097689"
---
# <a name="c-floating-point-constants"></a>Konstanty jazyka C s plovoucí desetinnou čárkou

"S plovoucí desetinnou čárkou konstanta" je desetinné číslo představující reálné číslo se znaménkem. Reprezentace reálné číslo se znaménkem obsahuje celočíselnou část desetinné části a exponent. Konstanty s plovoucí desetinnou čárkou použijte k reprezentaci hodnoty s plovoucí desetinnou čárkou, které se nedá změnit.

## <a name="syntax"></a>Syntaxe

*konstanta plovoucí desetinnou*: &nbsp; &nbsp; *desetinná konstanta exponent – část*<sub>optimalizované</sub> *s plovoucí desetinnou čárkou přípona* <sub>optimalizované</sub> &nbsp; &nbsp; *plovoucí desetinné části exponentu sekvence číslic suffix*<sub>optimalizované</sub>

*desetinná konstanta*: &nbsp; &nbsp; *sekvence číslic*<sub>optimalizované</sub> **.** *sekvence číslic* &nbsp; &nbsp; *sekvence číslic***.** 

*exponent část*: &nbsp; &nbsp; **e***přihlašování*<sub>optimalizované</sub> *sekvence číslic* &nbsp; &nbsp; **E***přihlašování*<sub>optimalizované</sub> *sekvence číslic* 

*znaménko* : jeden z &nbsp; &nbsp; **+ -**

*sekvence číslic*: &nbsp; &nbsp; *číslice* &nbsp; &nbsp; *sekvence číslic číslice*

*číslo s plovoucí čárkou přípona* : jeden z &nbsp; &nbsp; **f l F L**

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