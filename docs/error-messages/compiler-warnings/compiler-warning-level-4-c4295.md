---
title: "Kompilátoru (úroveň 4) upozornění C4295 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4295
dev_langs: C++
helpviewer_keywords: C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5815aab6163c7dc6ffa8bf89bbf56259724d02b5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4295"></a>C4295 kompilátoru upozornění (úroveň 4)
  
> '*pole*': pole je příliš malá, aby zahrnují ukončující znak hodnoty null  
  
 Byl inicializován pole, ale jeho poslední znak v poli není null; přístup k poli může vést k neočekávaným výsledkům.  
  
## <a name="example"></a>Příklad  
  
 Následující ukázka generuje C4295. Chcete-li tento problém vyřešit, je může deklarovat velikosti pole větší pro uložení ukončující z inicializátoru hodnotu null.  
  
```C  
// C4295.c  
// compile with: /W4  
  
int main() {  
   char a[3] = "abc";   // C4295  
}  
```