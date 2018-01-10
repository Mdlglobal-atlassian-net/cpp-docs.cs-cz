---
title: FpCsr | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: dff95d5d-7589-4432-82db-64b459c24352
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 15b7caebc99c4724c0e28b7812da8ef224184385
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fpcsr"></a>FpCsr
Stav registru také obsahuje x87 FPU řídicího slova. Konvence volání určí tento registr stálým.  
  
 Spuštění programu x87 FPU kontrolní slovo registru je nastavena na tyto standardní hodnoty na začátku:  
  
```  
FPCSR[0:6]: Exception masks all 1's (all exceptions masked)  
FPCSR[7]: Reserved - 0  
FPCSR[8:9]: Precision Control - 10B (double precision)  
FPCSR[10:11]: Rounding  control - 0 (round to nearest)  
FPCSR[12]: Infinity control - 0 (not used)  
```  
  
 Volaný, který mění žádná pole v rámci FPCSR musí obnovit před návratem do jeho volajícího. Kromě toho volající, který změní některé z těchto polí musí obnovit na standardní hodnoty před vyvoláním volaného, pokud dohodou volaného očekává upravené hodnoty.  
  
 Existují dvě výjimky pravidla týkající se bez volatility příznaky ovládacích prvků:  
  
1.  Ve funkcích, kde zdokumentovaných účel dané funkce stálé FpCsr příznaků.  
  
2.  Pokud je prokazatelně správné, že porušení těchto pravidel výsledky v programech, které se chovají/znamenají stejně jako program, kde nejsou porušena tato pravidla, například prostřednictvím analýzy celého programu.  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../build/calling-convention.md)