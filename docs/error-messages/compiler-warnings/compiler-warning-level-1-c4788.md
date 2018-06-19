---
title: Kompilátoru (úroveň 1) upozornění C4788 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4788
dev_langs:
- C++
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19a43fb9d79c63637b2bff9a27661a9f848ef6dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284196"
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