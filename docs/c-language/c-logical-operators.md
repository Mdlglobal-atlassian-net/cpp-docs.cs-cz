---
title: Logické operátory jazyka C
ms.date: 06/14/2018
helpviewer_keywords:
- logical operators, expression sequence points
- logical operators, C
- logical AND operator
- '|| operator'
- operators [C], logical
- short-circuit evaluation
- '&& operator'
- logical OR operator
ms.assetid: c0a4e766-ad56-4300-bf76-b28dc0e19b43
ms.openlocfilehash: 5df0c0f16bdf298c47a6a0699ec10c7392ab84ca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651266"
---
# <a name="c-logical-operators"></a>Logické operátory jazyka C

Logické operátory provádí logické- a (**&&**) a logical-OR (**||**) operace.

## <a name="syntax"></a>Syntaxe

*logický a výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Inkluzivní nebo výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický a výraz***&&***včetně výraz OR* 

*logický výraz OR*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický a výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický výraz OR***&#124;&#124;***logické a expression* 

## <a name="remarks"></a>Poznámky

Logické operátory neprovádějte obvyklé aritmetické převody. Místo toho vyhodnotit operandem z hlediska jeho ekvivalence na hodnotu 0. Výsledkem operace na logické je 0 nebo 1. Výsledný typ je **int**.

Logické operátory jazyka C jsou popsané níže:

|Operátor|Popis|
|--------------|-----------------|
|**&&**|Logický- a operátor vytvoří hodnotu 1, pokud mají oba operandy nenulové hodnoty. Pokud některý operand je rovna 0, výsledkem je 0. Pokud první operand logické- a operace se rovná 0, je druhý operand, nebude hodnocen.|
|**&#124;&#124;**|Logický operátor nebo operátor provádí operaci inkluzivní operátor OR na jeho operandy. Výsledkem je 0, pokud mají oba operandy hodnoty 0. Pokud některý operand má nenulovou hodnotu, výsledek je 1. Pokud je první operand operace logického operátoru OR má nenulovou hodnotu, není vyhodnocen Druhý operand.|

Operandy logického- a a logický operátor OR výrazy jsou vyhodnocovány zleva doprava. Pokud hodnotu prvního operandu stačí určit výsledek operace, není vyhodnocen Druhý operand. Tento postup se nazývá "zkrácené vyhodnocení". Po prvním operandem je bod sekvence. Zobrazit [body sekvence](../c-language/c-sequence-points.md) Další informace.

## <a name="examples"></a>Příklady

Následující příklady ilustrují logické operátory:

```C
int w, x, y, z;

if ( x < y && y < z )
    printf( "x is less than z\n" );
```

V tomto příkladu **printf** tisknout zprávu, pokud je volána funkce `x` je menší než `y` a `y` je menší než `z`. Pokud `x` je větší než `y`, druhý operand (`y < z`), nebude hodnocen a nic se nevytiskne. Všimněte si, že to může způsobit problémy v případech, kdy Druhý operand má vedlejší účinky, které jsou právě spoléhat nějakého jiného důvodu.

```C
printf( "%d" , (x == w || x == y || x == z) );
```

V tomto příkladu Pokud `x` rovná buď `w`, `y`, nebo `z`, aby druhý argument **printf** funkce vyhodnotí jako true a vypsání hodnoty 1. V opačném případě je vyhodnocen jako NEPRAVDA a vytisknout hodnotu 0. Poté, co byla jedna z podmínek vyhodnotí jako true, přestane hodnocení.

## <a name="see-also"></a>Viz také:

- [Logický operátor AND: &&](../cpp/logical-and-operator-amp-amp.md)
- [Logický operátor OR:&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)
