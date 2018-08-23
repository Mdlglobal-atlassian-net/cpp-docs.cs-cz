---
title: Upozornění (úroveň 1) C4788 kompilátoru | Dokumentace Microsoftu
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
ms.openlocfilehash: 23e86de5ebab3f99c7d98e502e280b5defb51e10
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465108"
---
# <a name="compiler-warning-level-1-c4788"></a>Kompilátor upozornění (úroveň 1) C4788
'identifier': identifikátor se zkrátil na znaků 'number'  
  
 Kompilátor omezuje maximální délku povolenou pro název funkce. Když kompilátor generuje funclets pro kód EH/SEH, tvoří název funkce předponou v podobě název funkce nějaký text, například "__catch", "\__unwind", nebo jiného řetězce.  
  
 Výsledný název funkce může být příliš dlouhý a bude ji zkrátit a generovat C4788 kompilátor.  
  
 Pokud chcete vyřešit toto upozornění, zkraťte název původní funkce. Pokud je funkce C++ šablony funkce nebo metoda, pomocí definice typu pro část názvu. Příklad:  
  
```  
C1<x, y, z<T>>::C2<a,b,c>::f  
```  
  
 lze nahradit:  
  
```  
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;  
new_class::f  
```  
  
 Toto upozornění se zobrazí pouze v x64 kompilátoru.