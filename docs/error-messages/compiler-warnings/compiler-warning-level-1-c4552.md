---
title: "Kompilátoru (úroveň 1) upozornění C4552 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4552
dev_langs: C++
helpviewer_keywords: C4552
ms.assetid: ebbbb5ee-1c19-45bd-b386-41a19630fc76
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6e7b19b59653d8fa670bddf8674051422b94cf1e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4552"></a>C4552 kompilátoru upozornění (úroveň 1)
'operátor': operátor nemá žádný vliv; Očekávaný operátoru s vedlejším účinkem  
  
 Pokud příkaz výrazu operátor s žádné vedlejším účinkem jako horní části výrazu, je pravděpodobně chyba.  
  
 Pokud chcete přepsat toto upozornění, uveďte výrazu v závorkách.  
  
 Následující ukázka generuje C4552:  
  
```  
// C4552.cpp  
// compile with: /W1  
int main() {  
   int i, j;  
   i + j;   // C4552  
   // try the following line instead  
   // (i + j);  
}  
```