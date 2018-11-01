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
ms.openlocfilehash: 2133aaa5faa0f4bef7391fb5c0e7e0eb51fd4e69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543364"
---
# <a name="c-bitwise-operators"></a>Bitové operátory jazyka C

Bitové operátory provádějí operace bitový- a (**&**), bitový exkluzivní OR (**^**) a bitový inkluzivní OR (**&#124;**) operace.

## <a name="syntax"></a>Syntaxe

*Výraz AND*: &nbsp; &nbsp; *výrazu rovnosti* &nbsp; &nbsp; *výraz AND* **&** *výrazu rovnosti*

*výraz exkluzivní OR*: &nbsp; &nbsp; *výraz AND* &nbsp; &nbsp; *výraz exkluzivní OR* **^** *Výraz AND*

*Inkluzivní výraz OR*: &nbsp; &nbsp; *výraz exkluzivní OR* &nbsp; &nbsp; *včetně výraz OR* &#124; *výraz exkluzivní OR*

Operandy bitové operátory musí mít integrální typy, ale jejich typy se může lišit. Tyto operátory provádějí obvyklé aritmetické převody Typ výsledku je typ operandu po převodu.

Bitové operátory jazyka C jsou popsané níže:

|Operátor|Popis|
|--------------|-----------------|
|**&**|Bitový – a operátor porovnává každý bit jeho prvního operandu s odpovídajícím bitem jeho druhého operandu. Pokud i službu bits 1, odpovídající bit výsledku je nastavená na 1. V opačném případě je odpovídající výsledek bit nastaven na hodnotu 0.|
|**^**|Operátor bitového operátoru OR porovnává každý bit jeho prvního operandu s odpovídajícím bitem jeho druhého operandu. Pokud jeden bit na hodnotu 0 a dalších bit na hodnotu 1, odpovídající bit výsledku je nastavená na 1. V opačném případě je odpovídající výsledek bit nastaven na hodnotu 0.|
|**&#124;**|Operátor bitového operátorem OR porovnává každý bit jeho prvního operandu s odpovídajícím bitem jeho druhého operandu. Pokud buď bit na hodnotu 1, odpovídající bit výsledku je nastavená na 1. V opačném případě je odpovídající výsledek bit nastaven na hodnotu 0.|

## <a name="examples"></a>Příklady

Následující tři příklady používají tyto deklarace:

```C
short i = 0xAB00;
short j = 0xABCD;
short n;

n = i & j;
```

Výsledek přiřazená `n` tento první příklad je stejný jako `i` (0xAB00 šestnáctkové).

```C
n = i | j;

n = i ^ j;
```

Bitový inkluzivní OR v druhém příkladu výsledkem hodnota 0xABCD (šestnáctkově), zatímco bitový exkluzivní OR v třetí příklad vytváří 0xCD (šestnáctkově).

**Specifické pro Microsoft**

Výsledky bitová operace na celá čísla se znaménkem, je definováno implementací podle standardu ANSI C. Kompilátor Microsoft C bitových operací s celými čísly se znaménkem fungují stejně jako bitové operace s celými čísly bez znaménka. Například `-16 & 99` může být vyjádřena v binárním souboru jako

```Expression
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

Výsledkem bitové operace AND je 96 decimal.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Bitový operátor AND: &](../cpp/bitwise-and-operator-amp.md)<br/>
[Bitový exkluzivní operátor OR: ^](../cpp/bitwise-exclusive-or-operator-hat.md)<br/>
[Bitový inkluzivní operátor OR:&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)