---
title: "Kompilátoru (úroveň 1) upozornění C4010 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4010
dev_langs: C++
helpviewer_keywords: C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b6a0c84d5138cf2ae8a7a6279d9dc0fde9fe9512
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4010"></a>C4010 kompilátoru upozornění (úroveň 1)
Komentář jeden řádek obsahuje znak pokračování řádku  
  
 Komentář jeden řádek, který je zavedený / /, obsahuje zpětné lomítko (\\) sloužícím jako znak pokračování řádku. Kompilátor za pokračování na další řádek a zpracovává jako komentář.  
  
 Některé syntaxe směrované editory neoznačují řádek následující znak pokračování jako komentář. Syntaxe zvýrazňování na všechny řádky, které způsobí toto upozornění ignorujte.  
  
 Následující ukázka generuje C4010:  
  
```  
// C4010.cpp  
// compile with: /WX  
int main() {  
   // the next line is also a comment because of the backslash \  
   int a = 3; // C4010  
   a++;  
}  
```