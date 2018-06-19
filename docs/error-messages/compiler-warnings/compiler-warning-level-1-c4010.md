---
title: Kompilátoru (úroveň 1) upozornění C4010 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4010
dev_langs:
- C++
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06ab6307a34887fe2d8a8719e20c31da9728664b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274651"
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