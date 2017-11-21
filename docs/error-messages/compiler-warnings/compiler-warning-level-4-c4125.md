---
title: "Kompilátoru (úroveň 4) upozornění C4125 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4125
dev_langs: C++
helpviewer_keywords: C4125
ms.assetid: a081d1f4-0789-4915-91df-7ff0b28ca245
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0de58fc029fe68d2734e0fa13e687f8012899081
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4125"></a>C4125 kompilátoru upozornění (úroveň 4)
Desítková číslice ukončí osmičková řídicí sekvence  
  
 Kompilátor vyhodnotí číslo osmičková bez číslici desítkové soustavy a předpokládá, že znaku je desítková číslice.  
  
## <a name="example"></a>Příklad  
  
```  
// C4125a.cpp  
// compile with: /W4  
char array1[] = "\709"; // C4125  
int main()  
{  
}  
```  
  
 Pokud číslici 9 slouží jako znak, opravte příklad následujícím způsobem:  
  
```  
// C4125b.cpp  
// compile with: /W4  
char array[] = "\0709";  // C4125 String containing "89"  
int main()  
{  
}  
```