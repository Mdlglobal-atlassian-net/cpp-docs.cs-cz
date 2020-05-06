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
ms.openlocfilehash: 5e17490926ee328c3a4ca03b1de9cb6e752959a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325674"
---
# <a name="c-floating-point-constants"></a>Konstanty jazyka C s plovoucí desetinnou čárkou

Konstanta s plovoucí desetinnou čárkou je desítkové číslo, které představuje číslo se znaménkem v čísle. Reprezentace čísla se znaménkem (reálné číslo) obsahuje celočíselnou část, zlomkovou část a exponent. Použijte konstanty s plovoucí desetinnou čárkou k vyjádření hodnot s plovoucí desetinnou čárkou, které nelze změnit.

## <a name="syntax"></a>Syntaxe

*plovoucí desetinná*čárka – konstanta:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*zlomek – konstanta* *exponentu –* volitelná<sub>možnost souhlasu</sub> *s plovoucí příponou*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;exponent *číselné sekvence* – *část* s *plovoucí desetinnou čárkou*– možnost<sub>výslovného</sub> názvu

*zlomková konstanta*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<sub>výslovný souhlas</sub> *číselné posloupnosti* **.** *sekvence číslic*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekvence číslic*  **.**

*exponent – část*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**e** *symbol*<sub>opt</sub> e *-číslice opt – posloupnost*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**E** *Symbol*<sub>opt</sub> E *-číslice opt – posloupnost*

*Sign*: jedna z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**+ -**

*sekvence číslic*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*základní*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;číslice *sekvence číslic* *digit*

*plovoucí přípona*: jedna z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**f l F L**

Můžete vynechat číslice před desetinnou čárkou (celočíselnou část hodnoty) nebo číslicemi za desetinnou čárkou (zlomkovou část), ale ne obojí. Desetinnou čárku můžete opustit pouze v případě, že zadáte exponent. Žádné prázdné znaky nemohou oddělovat číslice nebo znaky konstanty.

Následující příklady ilustrují některé formy konstant a výrazů s plovoucí desetinnou čárkou:

```C
15.75
1.575E1   /* = 15.75   */
1575e-2   /* = 15.75   */
-2.5e-3   /* = -0.0025 */
25E-4     /* =  0.0025 */
```

Konstanty s plovoucí desetinnou čárkou jsou kladné, pokud nejsou předcházejí znaménkem mínus (**-**). V tomto případě se znaménko mínus považuje za unární operátor aritmetické negace. Konstanty s plovoucí desetinnou `float`čárkou mají typ, `double`nebo `long double`.

Konstanta s plovoucí desetinnou čárkou bez přípony **f**, **f**, **l**nebo **l** je `double`typu. Pokud je písmeno **f** nebo **f** příponou, konstanta je typu `float`. Pokud je přípona v písmenu **l** nebo **l**, má typ `long double`. Příklad:

```C
10.0L  /* Has type long double  */
10.0F  /* Has type float        */
```

Všimněte si, že kompilátor jazyka Microsoft C `long double` interně reprezentuje stejný `double`typ jako typ. Informace o typu `double`, a `float` `long double`jsou uvedeny v části [úložiště základních typů](../c-language/storage-of-basic-types.md) .

Můžete vynechat celočíselnou část konstanty s plovoucí desetinnou čárkou, jak je znázorněno v následujících příkladech. Číslo. 75 lze vyjádřit mnoha způsoby, včetně následujících:

```C
.0075e2
0.075e1
.075e1
75e-2
```

## <a name="see-also"></a>Viz také

[Konstanty jazyka C](../c-language/c-constants.md)
