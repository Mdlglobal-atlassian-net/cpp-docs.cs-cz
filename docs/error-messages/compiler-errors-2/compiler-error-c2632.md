---
title: "C2632 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2632
dev_langs:
- C++
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 03a6d75ab9af6cd45ef982ff9d2e12640266c1b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2632"></a>C2632 chyby kompilátoru
'type1' a 'type2' je neplatný.  
  
 Tato chyba může být způsobena, pokud chybí kód mezi dvěma specifikátory typu.  
  
 Následující ukázka generuje C2632:  
  
```  
// C2632.cpp  
int float i;   // C2632  
```  
  
 Tato chyba může také vygenerovaného jako výsledek kompilátoru shoda práci, kterou bylo provedeno pro Visual Studio .NET 2003. `bool`je nyní správný typ. V předchozích verzích `bool` byl definice typu a můžete vytvořit identifikátory s tímto názvem.  
  
 Následující ukázka generuje C2632:  
  
```  
// C2632_2.cpp  
// compile with: /LD  
void f(int bool);   // C2632  
```  
  
 Chcete-li tuto chybu vyřešit tak, aby kód je platný v sadě Visual Studio .NET 2003 i sady Visual Studio .NET verzí aplikace Visual C++, přejmenujte identifikátor.