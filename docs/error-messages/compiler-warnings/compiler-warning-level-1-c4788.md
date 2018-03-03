---
title: "Kompilátoru (úroveň 1) upozornění C4788 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4788
dev_langs:
- C++
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e6f876dada851f46b7708ef1b34da4bae6f96dc0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4788"></a>C4788 kompilátoru upozornění (úroveň 1)
"identifikátor": identifikátor byl zkrácen na "číslo" znaků  
  
 Kompilátor omezuje maximální délku povolenou pro název funkce. Pokud kompilátor vygeneruje funclets pro EH/SEH kód, tvoří název funclet předponou názvu funkce s nějaký text, například "__catch", "\__unwind", nebo jiný řetězec.  
  
 Výsledný název funclet může být příliš dlouho a bude zkrácení a generovat C4788 kompilátoru.  
  
 Chcete-li vyřešit toto upozornění, zmenšit na původní název funkce. Pokud funkci C++ šablony funkce nebo metoda, použijte pro část názvu definice typu. Příklad:  
  
```  
C1<x, y, z<T>>::C2<a,b,c>::f  
```  
  
 lze nahradit:  
  
```  
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;  
new_class::f  
```  
  
 Toto upozornění se zobrazí jenom v [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] kompilátoru.