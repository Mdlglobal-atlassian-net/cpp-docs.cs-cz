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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326583"
---
# <a name="c-logical-operators"></a>Logické operátory jazyka C

Logické operátory provádějí operace logického a (**&&**) a logického operátoru**||** or ().

## <a name="syntax"></a>Syntaxe

*logický operátor and-Expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz (včetně)*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz logického operátoru and a Expression*  **&&**  *(včetně)*

*logický výraz or*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logický operátor AND-Expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;logický operátor *OR* **&#124;&#124;** *logický operátor and-Expression*    

## <a name="remarks"></a>Poznámky

Logické operátory neprovádějí běžné aritmetické převody. Místo toho vyhodnotí každý operand z pohledu jeho ekvivalence na hodnotu 0. Výsledek logické operace je 0 nebo 1. Typ výsledku je **int**.

Logické operátory jazyka C jsou popsány níže:

|Operátor|Popis|
|--------------|-----------------|
|**&&**|Logický operátor AND vytvoří hodnotu 1, pokud mají oba operandy nenulové hodnoty. Pokud je jeden operand roven 0, je výsledek 0. Pokud je první operand logického operátoru a operace rovna 0, druhý operand není vyhodnocen.|
|**&#124;&#124;**|Logický operátor OR provádí u operandů operaci zahrnující nebo. Výsledkem je 0, pokud oba operandy mají 0 hodnot. Pokud má jeden operand nenulovou hodnotu, je výsledkem hodnota 1. Pokud první operand logického nebo operace má nenulovou hodnotu, druhý operand není vyhodnocen.|

Operandy logických a logických výrazů jsou vyhodnocovány zleva doprava. Pokud je hodnota prvního operandu dostačující k určení výsledku operace, druhý operand se nevyhodnotí. Tento postup se nazývá "vyhodnocování krátkých okruhů". Za prvním operandem je sekvenční bod. Další informace naleznete v části [body sekvence](../c-language/c-sequence-points.md) .

## <a name="examples"></a>Příklady

Následující příklady ilustrují logické operátory:

```C
int w, x, y, z;

if ( x < y && y < z )
    printf( "x is less than z\n" );
```

V tomto příkladu je volána **funkce printf** k tisku `x` zprávy, pokud je menší než `y` a `y` je menší než. `z` Pokud `x` je větší než `y`, druhý operand (`y < z`) není vyhodnocen a nic není vytištěno. Všimněte si, že to může způsobit problémy v případech, kdy druhý operand má vedlejší účinky, na které se z nějakého důvodu spoléhaly.

```C
printf( "%d" , (x == w || x == y || x == z) );
```

V tomto příkladu, pokud `x` je rovna buď `w`, `y`nebo `z`, je druhý argument funkce **printf** vyhodnocen jako true a hodnota 1 je vytištěna. V opačném případě se vyhodnotí jako false a bude vytištěna hodnota 0. Jakmile se jedna z podmínek vyhodnotí jako true, vyhodnocování se zastaví.

## <a name="see-also"></a>Viz také

- [Logický operátor AND: &&](../cpp/logical-and-operator-amp-amp.md)
- [Logický operátor OR:  &#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)
