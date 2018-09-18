---
title: C relační operátory a operátory rovnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- relational operators, syntax
- equality operator
- operators [C], equality
- equality operator, syntax
- operators [C], relational
ms.assetid: c89a3815-a65e-4e0d-8333-0e8dc7fdb30b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1bf3c406059fe8744843e1353ad997acc19c499b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058234"
---
# <a name="c-relational-and-equality-operators"></a>Relační operátory a operátory rovnosti jazyka C

Binární relační operátory a operátory rovnosti porovnejte jejich prvního operandu s jejich druhého operandu k testování platnosti Zadaný vztah. Výsledek výrazu relační je 1, pokud testovaný vztah je PRAVDA a 0, pokud má hodnotu false. Typ výsledku je `int`.

**Syntaxe**

*relační výraz*: *shift-expression*

*relační výraz***\<***shift-expression* 

*relační výraz***>***shift-expression* 

*relační výraz***\<=***shift-expression* 

*relační výraz***>=***shift-expression* 

*výraz rovnosti*: *relační výraz*

*výraz rovnosti***==***relační výraz* 

*výraz rovnosti***! =***relační výraz* 

Relační operátory a operátory rovnosti testování následující vztahy:

|Operátor|Relace testování|
|--------------|-------------------------|
|**\<**|První operand menší než druhý operand|
|**>**|První operand větší než druhý operand|
|**\<=**|První operand menší než nebo rovna Druhý operand|
|**>=**|První operand větší než nebo rovna hodnotě Druhý operand|
|`==`|První operand rovna Druhý operand|
|`!=`|První operand nemá hodnotu druhého operandu|

V seznamu výše první čtyři operátory mají vyšší prioritu než operátory rovnosti (`==` a `!=`). Přečtěte si informace Priorita v tabulce [Priorita a asociativita operátorů jazyka C](../c-language/precedence-and-order-of-evaluation.md).

Operandy může mít typ integral, plovoucí nebo ukazatel. Typy operandů může lišit. Relační operátory provádět běžné aritmetické převody na typ s plovoucí desetinnou čárkou a celočíselné operandy. Kromě toho můžete použít následující kombinace typy operandů s relační operátory a operátory rovnosti:

- Odkazy na stejný typ může být operandy všechny relační nebo operátor rovnosti. Rovnost (`==`) a nerovnost (`!=`) operátory, výsledek porovnání určuje, zda dva odkazy adres stejné místo v paměti. Pro relační operátory (**\<**, **>**, **\<**=, a **>**=), výsledek porovnání určuje relativní pozice adresy paměti dvou objektů, na. Relační operátory porovnání pouze posunů.

     Porovnání ukazatelů je určená jenom pro části stejný objekt. V případě, že ukazatele odkazují na členy pole, je ekvivalentní k porovnání odpovídající dolní indexy porovnání. Adresa na první prvek pole je "menší než" adresa poslední prvek. V případě struktury ukazatelů na členy struktury deklarované později jsou "větší než" ukazatele na členy deklarované výše ve struktuře. Ukazatelé na členy stejné sjednocení jsou si rovny.

- Hodnota ukazatele je možné porovnat s konstantní hodnotou 0 rovnosti (`==`) nebo nerovnosti (`!=`). Ukazatel s hodnotou 0 se nazývá "null" ukazatel. To znamená ho neodkazuje na platný paměti umístění.

- Postupujte podle stejných pravidel jako relační operátory operátory rovnosti, ale povolit další možnosti: jde Porovnat ukazatel na celočíselný konstantní výraz s hodnotou 0 nebo na ukazatel na `void`. Pokud dva ukazatele jsou obě nulové ukazatele, jsou vyhodnoceny jako stejné. Operátory rovnosti porovnání segmentu a posun.

## <a name="examples"></a>Příklady

Následující příklady ilustrují relační operátory a operátory rovnosti.

```
int x = 0, y = 0;
if ( x < y )
```

Protože `x` a `y` jsou stejné, v tomto příkladu výraz vrací hodnotu 0.

```
char array[10];
char *p;

for ( p = array; p < &array[10]; p++ )
    *p = '\0';
```

Fragment v tomto příkladě nastaví všechny prvky objektu `array` na konstantu znaku null.

```
enum color { red, white, green } col;
   .
   .
   .
   if ( col == red )
   .
   .
   .
```

Tyto příkazy deklarujete proměnnou výčtu s názvem `col` se značkou `color`. V každém okamžiku může obsahovat proměnné celočíselnou hodnotu 0, 1 nebo 2, který představuje jeden z elementů výčet sady `color`: červená barva, prázdné nebo zelenou, v uvedeném pořadí. Pokud `col` obsahuje 0 při **Pokud** je proveden příkaz, všechny příkazy v závislosti na tom **Pokud** se spustí.

## <a name="see-also"></a>Viz také

[Relační operátory: \<, >, \<= a > =](../cpp/relational-operators-equal-and-equal.md)<br/>
[Operátory rovnosti: == a !=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)