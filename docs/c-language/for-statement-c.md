---
title: pro Statement (C) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6ad4b23e6caef15b5dabaaa3102d72e3ff84fbc
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860586"
---
# <a name="for-statement-c"></a>for – příkaz (C)

**Pro** příkaz umožňuje opakujte příkaz nebo složený příkaz zadaného počtu opakování. Text **pro** je proveden příkaz nulakrát nebo vícekrát, dokud nebude nepovinnou podmínku false. Volitelné výrazy můžete použít **pro** příkaz k inicializaci a změnit hodnoty během **pro** spuštění příkazu.

## <a name="syntax"></a>Syntaxe

*příkaz iterace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**pro** **(** *init-expression*<sub>optimalizované</sub> **;** *cond-expression*<sub>optimalizované</sub> **;** *výraz smyčky*<sub>optimalizované</sub> **)** *– příkaz*

Spuštění **pro** příkaz probíhá následujícím způsobem:

1. *Init-expression*, pokud existuje, je vyhodnocen. Toto nastavení určuje inicializaci smyčky. Neexistuje žádné omezení na typu *init-expression*.

1. *Cond-expression*, pokud existuje, je vyhodnocen. Tento výraz musí mít aritmetický typ nebo typ ukazatele. Vyhodnotí se před každou iteraci. Tří výsledků je možné:

   - Pokud *cond-expression* je **true** (nenulový), *příkaz* je spuštěn; potom *výraz smyčky*, pokud existuje, je vyhodnocen. *Výraz smyčky* je vyhodnocen po každé iteraci. Neexistuje žádné omezení na jeho typu. Vedlejší efekty bude vykonán v pořadí. Proces potom začne znovu vyhodnocením *cond-expression*.

   - Pokud *cond-expression* je vynechán, *cond-expression* je považován za hodnotu true a pokračuje v provádění přesně tak, jak je popsáno v předchozím odstavci. A **pro** příkaz bez *cond-expression* argument ukončí pouze tehdy, když **přerušení** nebo **vrátit** příkaz v rámci příkazu provede se tělo, nebo když **goto** (na označený příkaz mimo **pro** tělo s příkazy) provádí.

   - Pokud *cond-expression* je **false** (0), spuštění **pro** příkaz skončí a předá řízení dalšímu příkazu v programu.

A **pro** příkaz také skončí, když **přerušení**, **goto**, nebo **vrátit** je proveden příkaz v rámci těla příkazu. A **pokračovat** výroky **pro** smyčky způsobí, že *výraz smyčky* k vyhodnocení. Když **přerušení** uvnitř je proveden příkaz **pro** smyčky, *výraz smyčky* není vyhodnocování nebo provádění. Tento příkaz

```C
for( ; ; )
```

je obvyklé způsob, jak vytvořit nekonečnou smyčku, která může být pouze skončil s **přerušení**, **goto**, nebo **vrátit** příkazu.

## <a name="example"></a>Příklad

Tento příklad ukazuje, **pro** – příkaz:

```C
// c_for.c
int main()
{
   char* line = "H e  \tl\tlo World\0";
   int space = 0;
   int tab = 0;
   int i;
   int max = strlen(line);
   for (i = 0; i < max; i++ )
   {
      if ( line[i] == ' ' )
      {
          space++;
      }
      if ( line[i] == '\t' )
      {
          tab++;
      }
   }

   printf("Number of spaces: %i\n", space);
   printf("Number of tabs: %i\n", tab);
   return 0;
}
```

## <a name="output"></a>Výstup

```Output
Number of spaces: 4
Number of tabs: 2
```

## <a name="see-also"></a>Viz také

[Příkazy](../c-language/statements-c.md)
