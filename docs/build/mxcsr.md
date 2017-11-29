---
title: MxCsr | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 4f3c229d-0862-4733-acc7-9ed7a0b870ce
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6bbd0adbfa7ccc51093ac087d908360b893ea518
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mxcsr"></a>MxCsr
Stav registru obsahuje také MxCsr. Konvence volání tento registr rozděluje volatile část a stálou část. Volatile část se skládá z příznaků 6 stavu, MXCSR [0:5], zatímco zbytek registru, MXCSR [6:15], je považován za stálý.  
  
 Stálá část je nastaven na následující standardní hodnoty na začátku spuštění programu:  
  
```  
MXCSR[6]         : Denormals are zeros - 0  
MXCSR[7:12]      : Exception masks all 1's (all exceptions masked)  
MXCSR[13:14]   : Rounding  control - 0 (round to nearest)  
MXCSR[15]      : Flush to zero for masked underflow - 0 (off)  
```  
  
 Volaný, který mění libovolná stálá pole v rámci MXCSR musí obnovit před vrácením jeho volajícího. Kromě toho volající, který změní některé z těchto polí musí obnovit na standardní hodnoty před vyvoláním volaného, pokud dohodou volaného očekává upravené hodnoty.  
  
 Existují dvě výjimky pravidla týkající se bez volatility příznaky ovládacích prvků:  
  
-   Ve funkcích, kde zdokumentovaných účel dané funkce stálé MxCsr příznaků.  
  
-   Pokud je prokazatelně správné, že porušení těchto pravidel výsledky v programech, které se chovají/znamenají stejně jako program, kde nejsou porušena tato pravidla, například prostřednictvím analýzy celého programu.  
  
 Žádné předpoklady nelze realizovat týkající se stavu služby volatile části MXCSR přes hranice funkce, pokud není výslovně uvedeno v dokumentaci funkce.  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../build/calling-convention.md)