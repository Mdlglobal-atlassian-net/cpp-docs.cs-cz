---
title: MxCsr | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 4f3c229d-0862-4733-acc7-9ed7a0b870ce
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7794cea8906440c0adca94791d08e3ced6af747e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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