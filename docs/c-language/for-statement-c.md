---
title: pro Statement (C) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 18c2b89e8c09ca7ddb6ba7f2cc02c9b400265a35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="for-statement-c"></a>for – příkaz (C)
**Pro** příkaz umožňuje opakujte příkaz nebo složený příkaz zadaného počtu opakování. Text **pro** je spustit příkaz vícekrát nebo dokud nepovinnou podmínku se změní na hodnotu false. Volitelné výrazy v rámci můžete použít **pro** příkaz k inicializaci a změnit hodnoty během **pro** provádění příkazu společnosti.  
  
## <a name="syntax"></a>Syntaxe  
 *příkaz iterace*:  
 &nbsp;&nbsp;**pro** **(** *init výraz*<sub>opt</sub> **;** *podmíněného výrazu*<sub>opt</sub> **;** *smyčky výraz*<sub>opt</sub> **)** *– příkaz*  
  
 Spuštění **pro** příkaz pokračuje následujícím způsobem:  
  
1.  *Init výraz*, pokud existuje, vyhodnotí. Toto nastavení určuje inicializace smyčky. Neexistuje žádné omezení na typu *init výraz*.  
  
2.  *Podmíněného výrazu*, pokud existuje, vyhodnotí. Tento výraz musí mít typ aritmetické nebo ukazatel. Vyhodnotí před každé iteraci. Je možné, tři výsledky:  
  
    -   Pokud *podmíněného výrazu* je **true** (nenulové hodnoty), *příkaz* je provedeno; poté *smyčky výraz*, pokud existuje, vyhodnotí. *Smyčky výraz* vyhodnotí po každé iteraci. Neexistuje žádné omezení u jeho typu. Vedlejší efekty bude vykonán v pořadí. Proces potom začne znovu s vyhodnocení *podmíněného výrazu*.  
  
    -   Pokud *podmíněného výrazu* je vynechán, *podmíněného výrazu* považuje za hodnotu true a provádění procesu přesně jak je popsáno v předchozím odstavci. A **pro** příkaz bez *podmíněného výrazu* argument ukončí pouze tehdy, když **zalomení** nebo **vrátit** v rámci příkaz – příkaz provede se tělo, nebo když **goto** (pro příkaz s popiskem mimo **pro** těla příkazu) se spustí.  
  
    -   Pokud *podmíněného výrazu* je **false** (0), provádění **pro** příkaz ukončí a předá řízení další příkaz v programu.  
  
 A **pro** příkaz taky ukončí, kdy **zalomení**, **goto**, nebo **vrátit** se spustí příkaz do těla příkazu. A **pokračovat** příkaz v **pro** cykly příčiny *smyčky výraz* k vyhodnocení. Při **zalomení** je spustit příkaz uvnitř **pro** ve smyčce, *smyčky výraz* není vyhodnocení nebo provést. Tento příkaz  
  
```  
for( ;; )  
```  
  
 je obvyklé způsob, jak vytvořit nekonečnou smyčku, která může být pouze skončil s **zalomení**, **goto**, nebo **vrátit** příkaz.  
  
## <a name="code"></a>Kód  
 Tento příklad ukazuje **pro** příkaz:  
  
```  
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
  
```  
Number of spaces: 4  
Number of tabs: 2  
```  
  
## <a name="see-also"></a>Viz také  
 [Příkazy](../c-language/statements-c.md)