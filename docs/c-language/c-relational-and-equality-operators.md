---
title: Relační operátory a operátory rovnosti jazyka C
ms.date: 10/18/2018
helpviewer_keywords:
- relational operators, syntax
- equality operator
- operators [C], equality
- equality operator, syntax
- operators [C], relational
ms.assetid: c89a3815-a65e-4e0d-8333-0e8dc7fdb30b
ms.openlocfilehash: 25e9bb65492e0c4b100ecd7a800491d238b1dd38
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400533"
---
# <a name="c-relational-and-equality-operators"></a>Relační operátory a operátory rovnosti jazyka C

Binární relační operátory a operátory rovnosti porovnávají svůj první operand s jejich druhým operandem k otestování platnosti zadaného vztahu. Výsledkem relačního výrazu je 1, pokud je testovaný vztah true a 0, pokud má hodnotu false. Typ výsledku je `int`.

**Syntaktick**

*relační výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Shift-Expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz* **&lt;** – *SHIFT-Expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz* **>** – *SHIFT-Expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz* ** &lt; ** – *SHIFT-Expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz* **>=** – *SHIFT-Expression*

*výraz rovnosti*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relační výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**==** *relační* výraz *rovnosti* – výraz<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*rovnost-Expression* **! =** *relační výraz*

Relační operátory a operátory rovnosti testují následující vztahy:

|Operátor|Testovaný vztah|
|--------------|-------------------------|
|**&lt;**|První operand méně než druhý operand|
|**>**|První operand větší než druhý operand|
|**&lt;=**|První operand je menší nebo roven druhému operandu.|
|**>=**|První operand, který je větší nebo roven druhému operandu|
|**==**|První operand rovný druhému operandu|
|**!=**|První operand nerovná se druhému operandu|

První čtyři operátory v seznamu výše mají vyšší prioritu než operátory rovnosti (`==` a `!=`). Podívejte se na informace o prioritách v [prioritě tabulky a asociativita operátorů jazyka C](../c-language/precedence-and-order-of-evaluation.md).

Operandy mohou mít celočíselný, plovoucí nebo typ ukazatele. Typy operandů můžou být odlišné. Relační operátory provádějí obvyklé aritmetické převody na celočíselných a plovoucích operandech typu. Kromě toho můžete použít následující kombinace typů operandů s operátory relačních a rovnosti:

- Oba operandy relačních operátorů nebo operátoru rovnosti mohou být ukazatele na stejný typ. Pro operátory rovnosti`==`() a nerovnosti`!=`() výsledek porovnání označuje, zda dva ukazatelé mají stejné umístění v paměti. U ostatních relačních operátorů**\<**( **>**, **\<**, = a **>**=) výsledek porovnání označuje relativní pozici dvou adres paměti objektů, na které ukazuje. Relační operátory porovnávají pouze posuny.

   Porovnání ukazatelů je definováno pouze pro části stejného objektu. Pokud ukazatelé odkazují na členy pole, porovnání je ekvivalentní porovnání odpovídajících dolních indexů. Adresa prvního prvku pole je "menší než" adresa posledního prvku. V případě struktur jsou ukazatelé na členy struktury, které jsou deklarovány později, "větší než" ukazatele na členy deklarované dříve ve struktuře. Ukazatele na členy stejného sjednocení jsou stejné.

- Hodnota ukazatele může být porovnána s konstantní hodnotou 0 pro rovnost (`==`) nebo nerovnost (`!=`). Ukazatel s hodnotou 0 se nazývá ukazatel "null"; To znamená, že neukazuje na platné umístění v paměti.

- Operátory rovnosti dodržují stejná pravidla jako relační operátory, ale umožňují další možnosti: ukazatel lze porovnat s konstantním integrálním výrazem s hodnotou 0 nebo ukazatelem na hodnotu `void`. Pokud dva ukazatele jsou ukazatele s hodnotou null, porovná se stejně. Operátory rovnosti porovnávají segment i posun.

## <a name="examples"></a>Příklady

Níže uvedené příklady ilustrují relační operátory a operátory rovnosti.

```C
int x = 0, y = 0;
if ( x < y )
```

Vzhledem `x` k `y` tomu, že a jsou stejné, výraz v tomto příkladu vypočítá hodnotu 0.

```C
char array[10];
char *p;

for ( p = array; p < &array[10]; p++ )
    *p = '\0';
```

Fragment v tomto příkladu nastaví jednotlivé prvky `array` na konstantu znaku null.

```C
enum color { red, white, green } col;
   .
   .
   .
   if ( col == red )
   .
   .
   .
```

Tyto příkazy deklaruje proměnnou výčtu s názvem `col` s tagem `color`. Proměnná může kdykoli obsahovat celočíselnou hodnotu 0, 1 nebo 2, která představuje jeden z prvků sady `color`výčtového typu: barva červenou, bílou nebo zelenou v uvedeném pořadí. Pokud `col` obsahuje hodnotu 0, pokud je proveden příkaz **if** , všechny příkazy v závislosti na tom, **zda** budou provedeny.

## <a name="see-also"></a>Viz také

[Relační operátory: \<, >, \<= a >=](../cpp/relational-operators-equal-and-equal.md)<br/>
[Operátory rovnosti: = = a! =](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)
