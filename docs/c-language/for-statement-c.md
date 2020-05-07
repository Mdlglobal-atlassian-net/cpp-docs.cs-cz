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

Příkaz **for** umožňuje opakování příkazu nebo složeného příkazu v zadaném počtu opakování. Tělo příkazu **for** se provede nula nebo vícekrát, dokud se nepovede volitelná podmínka NEPRAVDA. Můžete použít volitelné výrazy v rámci příkazu **for** pro inicializaci a změnu hodnot během provádění příkazu **for** .

## <a name="syntax"></a>Syntaxe

*příkaz iterace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**pro** **(** *init-expression*<sub>opt</sub> **;** *cond-expression*<sub>opt</sub> **;** *loop-expression*<sub>opt</sub> **)** – *příkaz*

Provedení příkazu **for** bude pokračovat následujícím způsobem:

1. Vyhodnotí se *init-expression*, pokud existuje. Určuje inicializaci smyčky. Typ *init-expression*není nijak omezen.

1. *Cond-expression*, pokud existuje, je vyhodnocen. Tento výraz musí mít aritmetický typ nebo typ ukazatele. Je vyhodnocen před každou iterací. Jsou možné tři výsledky:

   - Pokud je *cond-expression* **true** (nenulový), je proveden *příkaz* ; pak se vyhodnotí *výraz loop*(pokud existuje). *Výraz loop* je vyhodnocen po každé iteraci. Neexistuje žádné omezení typu. Vedlejší účinky budou provedeny v daném pořadí. Proces se pak znovu spustí s hodnocením *cond-expression*.

   - Pokud je *cond-expression* vynechán, *cond-expression* se považuje za true a provádění pokračuje přesně tak, jak je popsáno v předchozím odstavci. Příkaz **for** bez argumentu *cond-expression* končí pouze v případě, že je proveden příkaz **Break** nebo **return** v rámci těla příkazu, nebo při spuštění příkazu **goto** (na příkaz s popiskem mimo tělo příkazu **for** ).

   - Pokud *cond-expression* je **false** (0), provádění příkazu **for** se ukončí a řízení projde dalšímu příkazu v programu.

Příkaz **for** se také ukončí při provedení příkazu **Break**, **goto**nebo **return** v rámci těla příkazu. Příkaz **Continue** ve smyčce **for** způsobí vyhodnocení *výrazu loop-expression* . Pokud je příkaz **Break** proveden uvnitř smyčky **for** , *výraz smyčky* není vyhodnocen nebo proveden. Tento příkaz

```C
for( ; ; )
```

je vlastní způsob, jak vytvořit nekonečnou smyčku, která může být pouze ukončena příkazem **Break**, **goto**nebo **return** .

## <a name="example"></a>Příklad

Tento příklad ilustruje příkaz **for** :

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
