---
title: "Kompilátoru (úroveň 1) upozornění C4806 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4806
dev_langs: C++
helpviewer_keywords: C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1a9c9c48f01746aaf208db28ce84fe006e990aaf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4806"></a>C4806 kompilátoru upozornění (úroveň 1)
'operace': nebezpečné operace: žádná hodnota typu "typ" povýšit na typ "typ" může rovnat dané konstanta  
  
 Tato zpráva varuje před kódu, jako `b == 3`, kde `b` má typ `bool`. Povýšení pravidla Příčina `bool` má být převeden na `int`. To je povoleno, ale může být nikdy **true**. Následující ukázka generuje C4806:  
  
```  
// C4806.cpp  
// compile with: /W1  
int main()  
{  
   bool b = true;  
   // try..  
   // int b = true;  
  
   if (b == 3)   // C4806  
   {  
      b = false;  
   }  
}  
```