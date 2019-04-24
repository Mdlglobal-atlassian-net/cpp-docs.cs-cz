---
title: for – příkaz (C)
ms.date: 11/04/2016
helpviewer_keywords:
- for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
ms.openlocfilehash: df00bcab2f9f9e51a6f37e19670b6cd240fa5cc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233641"
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

## <a name="see-also"></a>Viz také:

[Příkazy](../c-language/statements-c.md)
