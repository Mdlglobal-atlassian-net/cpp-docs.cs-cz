---
title: Bitové operátory jazyka C
ms.date: 01/29/2018
helpviewer_keywords:
- '| operator, bitwise operators'
- bitwise operators, Visual C
- bitwise operators
- operators [C], bitwise
- ^ operator, bitwise operators
- AND operator
- ampersand operator (&)
- ^ operator
- '& operator, bitwise operators'
ms.assetid: e22127b1-9a2d-4876-b01d-c8f72cec3317
ms.openlocfilehash: 50be8ae38f21d0a9f46c180abf179e1358b707cd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168770"
---
# <a name="c-bitwise-operators"></a>Bitové operátory jazyka C

Bitové operátory provádějí operace bitového operátoru**&** and (), bitového operátoru**^** or () a bitového i (**&#124;**).

## <a name="syntax"></a>Syntaxe

*And-Expression*: &nbsp; &nbsp;rovnost *-Expression* &nbsp; &nbsp; *a-* **&** Expression *rovnost-* Expression

Exclusive *-or-Expression*: &nbsp; &nbsp; *a-* &nbsp; &nbsp;Expression *Exclusive-nebo-* **^** Expression *a-Expression*

*výraz (včetně) nebo*výrazu &nbsp;: &nbsp; *exclusive-or-Expression* &nbsp; &nbsp; *, včetně nebo* Expression &#124; *Exclusive-* or-Expression

Operandy bitových operátorů musí mít celočíselné typy, ale jejich typy můžou být odlišné. Tyto operátory provádějí obvyklé aritmetické převody; Typ výsledku je typ operandů po převodu.

Bitové operátory jazyka C jsou popsány níže:

|Operátor|Popis|
|--------------|-----------------|
|**&**|Bitový operátor AND porovnává každý bit svého prvního operandu s odpovídajícím bitem jeho druhého operandu. Pokud jsou obě bity 1, odpovídající bit výsledku je nastaven na hodnotu 1. V opačném případě je odpovídající bit výsledek nastaven na hodnotu 0.|
|**^**|Bitový operátor OR porovnává každý bit jeho prvního operandu s odpovídajícím bitem jeho druhého operandu. Pokud je jeden bit 0 a druhý bit je 1, odpovídající bit výsledku je nastaven na hodnotu 1. V opačném případě je odpovídající bit výsledek nastaven na hodnotu 0.|
|**&#124;**|Bitový operátor OR porovnává každý bit jeho prvního operandu s odpovídajícím bitem jeho druhého operandu. Pokud má bit hodnotu 1, odpovídající bit výsledku je nastaven na hodnotu 1. V opačném případě je odpovídající bit výsledek nastaven na hodnotu 0.|

## <a name="examples"></a>Příklady

Tyto deklarace se používají v následujících třech příkladech:

```C
short i = 0xAB00;
short j = 0xABCD;
short n;

n = i & j;
```

Výsledek přiřazený `n` v tomto prvním příkladu je stejný jako `i` (0xAB00 šestnáctkový).

```C
n = i | j;

n = i ^ j;
```

Bitový a v druhém příkladu má za následek hodnotu 0xABCD (šestnáctkový), zatímco bitový-výhradní nebo třetí příklad vytvoří 0xCD (šestnáctkový).

**Specifické pro Microsoft**

Výsledky bitové operace u celých čísel se znaménkem jsou implementovány podle standardu ANSI C. V případě kompilátoru jazyka Microsoft C fungují bitové operace s podepsanými celými čísly stejně jako bitové operace u celých čísel bez znaménka. Například `-16 & 99` lze vyjádřit v binárním formátu jako

```Expression
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

Výsledek bitového operátoru AND je 96 desetinných míst.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Bitový operátor AND: &](../cpp/bitwise-and-operator-amp.md)<br/>
[Bitový exkluzivní operátor OR: ^](../cpp/bitwise-exclusive-or-operator-hat.md)<br/>
[Bitový operátor OR: &#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)
