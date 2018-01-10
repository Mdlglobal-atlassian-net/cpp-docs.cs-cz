---
title: Dot direktivy | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, dot directives
- dot directives in NMAKE
ms.assetid: ab35da65-30b6-48b7-87d6-61503d7faf9f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9958b13a6f06b0024ec2d4dd304abfe93b16741e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dot-directives"></a>Direktivy s tečkou
Zadejte direktivy s tečkou mimo blok popis na začátku řádku. Direktivy s tečkou začínat tečkou (. ) a jsou následovaným dvojtečkou (:). Jsou povoleny mezery a karty. Direktivy názvy tečkou se rozlišují malá a velká písmena.  
  
|– Direktiva|Účel|  
|---------------|-------------|  
|**. IGNORUJTE:**|Ignoruje nenulový ukončovací kód vrátí příkazy z místa, které jsou zadány na konec objektu souboru pravidel. Ve výchozím nastavení NMAKE zastaví, pokud příkaz vrátí nenulový ukončovací kód. K obnovení, kontroly chyb, použijte **! Cmdswitches –**. Ignorovat ukončovací kód pro jeden příkaz, použijte modifikátor pomlčky (-). Chcete-li ignorovat ukončovací kód pro celý soubor, použijte / I.|  
|**. DRAHÝCH:** *cíle*|Zachovává *cíle* na disku při zastavení jsou příkazy k jejich aktualizaci; nemá vliv, pokud příkaz přerušení zpracovává odstraněním souboru. Cílové názvy oddělujte mezery nebo karty. Ve výchozím nastavení odstraní NMAKE cíl, pokud dojde k přerušení sestavení CTRL + C nebo CTRL + BREAK. Každý použití **. DRAHOCENNÝ** se vztahují na celou makefile; více specifikace jsou kumulativní.|  
|**. TICHOU:**|Potlačí zobrazení spuštění příkazů z místa, které jsou zadány na konec objektu souboru pravidel. Ve výchozím nastavení zobrazí NMAKE příkazy, které vyvolá. Pokud chcete obnovit, zobrazování, použijte **! Cmdswitches –**. Chcete-li potlačit zobrazení do jednoho příkazu, použijte  **@**  modifikátor. K potlačení odezva pro celý soubor, použijte/S.|  
|**. PŘÍPONY:**`list`|Obsahuje seznam rozšíření pro odvozené pravidlo odpovídající; předdefinované zahrnují následující přípony: .exe .obj .asm .c sada .cxx BAS .cbl .for .pas .res .rc .f .f90|  
  
 Chcete-li změnit **. PŘÍPONY** seznamu pořadí nebo pokud chcete zadat nový seznam, vymažte seznamu a zadejte nové nastavení. Vymazání seznamu, zadejte po dvojtečkou se žádné přípony:  
  
```  
.SUFFIXES :  
```  
  
 Chcete-li přidat další přípony na konec seznamu, zadejte  
  
```  
.SUFFIXES : suffixlist  
```  
  
 kde *suffixlist* je seznam další přípony, oddělených mezery nebo karty. Chcete-li zobrazit aktuální nastavení **. PŘÍPONY**, spusťte s parametrem/p. NMAKE  
  
## <a name="see-also"></a>Viz také  
 [NMAKE – referenční zdroje](../build/nmake-reference.md)