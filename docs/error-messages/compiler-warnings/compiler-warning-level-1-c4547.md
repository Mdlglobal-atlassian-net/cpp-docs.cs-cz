---
title: "Kompilátoru (úroveň 1) upozornění C4547 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4547
dev_langs: C++
helpviewer_keywords: C4547
ms.assetid: 3edf1c2e-c0d5-444d-ae83-44a7cce24bb2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f61c4075e8c41970cb72ca317373d7aeb4bddb02
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4547"></a>C4547 kompilátoru upozornění (úroveň 1)
'operátor': operátor před čárkou nemá žádný vliv; Očekávaný operátoru s vedlejším účinkem  
  
 Kompilátor zjištěna výraz nesprávně formátovaných čárkami.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. Další informace najdete v tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 Následující ukázka generuje C4547:  
  
```  
// C4547.cpp  
// compile with: /W1  
#pragma warning (default : 4547)  
int i = 0;  
int j = 1;  
int main() {  
   int l = (i != i,0);   // C4547  
   // try the following line instead  
   // int l = (i != i);  
   // or  
   // int l = ((void)(i != i),0);  
}  
```