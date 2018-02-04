---
title: "Bitové operátory jazyka C | Microsoft Docs"
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 81498cfcc2dc93c407bfde5e9d832a9abdeab970
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2018
---
# <a name="c-bitwise-operators"></a>Bitové operátory jazyka C

Bitové operátory provést bitový- a (**&**), bitový exkluzivní OR (**^**) a bitové – včetně OR (**&#124;**) operace.

## <a name="syntax"></a>Syntaxe

*A výraz*:  
&nbsp;&nbsp;*equality-expression*  
&nbsp;&nbsp;*Výraz a*  **&**  *rovnosti – výraz*

*exclusive-OR-expression*:  
&nbsp;&nbsp;*AND – výraz*  
&nbsp;&nbsp;*výraz exkluzivní OR*  **^**  *a výraz*

*inclusive-OR-expression*:  
&nbsp;&nbsp;*exclusive-OR-expression*  
&nbsp;&nbsp;*včetně výraz OR* &#124; *výraz exkluzivní OR*

Operandy bitové operátory musí mít integrální typy, ale jejich typy mohou být různé. Obvyklé aritmetické převody; provést tyto operátory Typ výsledku je typ operandy po převodu.

Bitové operátory jazyka C jsou následující:

|Operátor|Popis|
|--------------|-----------------|
|**&**|Bitové hodnotě- a porovná každý bit jeho první operand odpovídající bit její druhý operand operátoru. Pokud jsou obě bits 1, 1 je nastavena odpovídající bit výsledek. Odpovídající bit výsledek, jinak hodnota nastavena na hodnotu 0.|
|**^**|Bitový exkluzivní OR operátor porovná každý bit jeho první operand odpovídající bit její druhý operand. Pokud je jeden bit 0 a dalších bit je 1, 1 je nastavena odpovídající výsledek bit. Odpovídající bit výsledek, jinak hodnota nastavena na hodnotu 0.|
|**&#124;**|Bitový – včetně-operátoru OR porovná každý bit jeho první operand odpovídající bit její druhý operand. Pokud je buď bit 1, odpovídající výsledek bit nastavená na 1. Odpovídající bit výsledek, jinak hodnota nastavena na hodnotu 0.|

## <a name="examples"></a>Příklady

Tyto deklarace se používají pro následující tři příklady:

```C
short i = 0xAB00;
short j = 0xABCD;
short n;

n = i & j;
```

Výsledek přiřazené `n` v této první příklad je stejný jako `i` (0xAB00 šestnáctkové).

```C
n = i | j;

n = i ^ j;
```

Bitový inkluzivní nebo v druhém příkladu výsledkem hodnota 0xABCD (hexadecimální), zatímco bitový exkluzivní OR v třetím příkladu vytvoří 0xCD (hexadecimální).

**Microsoft Specific**

Výsledky bitové operace na podepsaná celá čísla je definován implementace podle standardní ANSI C. Pro kompilátor Microsoft C bitové operace na podepsaná celá čísla fungovat stejně jako bitové operace na celá čísla bez znaménka. Například `-16 & 99` může být vyjádřený v binární soubor jako

```Expression
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

Výsledek bitové operace AND je 96 decimal.

**Konkrétní Microsoft END**

## <a name="see-also"></a>Viz také

[Bitový operátor AND: &](../cpp/bitwise-and-operator-amp.md)  
[Bitový exkluzivní operátor OR: ^](../cpp/bitwise-exclusive-or-operator-hat.md)  
[Bitový inkluzivní operátor OR: &#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)  