---
title: "Kompilátoru (úroveň 1) upozornění C4369 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4369
dev_langs: C++
helpviewer_keywords: C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3c0419908ed7d914196cd65d07a3fb43a16d75ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4369"></a>C4369 kompilátoru upozornění (úroveň 1)
'enumerátor': hodnotu výčtu 'Hodnota' nemůže být reprezentován jako "typ", hodnota je 'nová_hodnota.  
  
 Enumerátor výpočtu být větší než největší hodnota zadaného základního typu.  To způsobilo přetečení a kompilátor zabalená hodnota výčtu, která má nejnižší možná hodnota pro typ.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4369.  
  
```  
// C4369.cpp  
// compile with: /W1  
int main() {  
   enum Color: char { red = 0x7e, green, blue };   // C4369  
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK  
}  
```