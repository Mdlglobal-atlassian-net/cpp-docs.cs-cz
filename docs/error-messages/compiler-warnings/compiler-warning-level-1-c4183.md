---
title: "Kompilátoru (úroveň 1) upozornění C4183 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4183
dev_langs: C++
helpviewer_keywords: C4183
ms.assetid: dc48312c-4b34-44dd-80ff-eb5f11d5ca47
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 025509de5f2b3dd14d957422042d8094d137924f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4183"></a>C4183 kompilátoru upozornění (úroveň 1)
"identifikátor": chybí návratový typ; předpokládá, že vrácení, int, členské funkce  
  
 Definice vloženého členské funkce ve třídě nebo struktuře nemá návratový typ.. Tento člen funkci předpokládá, že mají výchozí návratový typ `int`.  
  
 Následující ukázka generuje C4183:  
  
```  
// C4183.cpp  
// compile with: /W1 /c  
#pragma warning(disable : 4430)  
class MyClass1;  
class MyClass2 {  
   MyClass1() {};   // C4183  
};  
```