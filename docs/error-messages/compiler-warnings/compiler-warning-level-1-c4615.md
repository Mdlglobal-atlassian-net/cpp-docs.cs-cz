---
title: "Kompilátoru (úroveň 1) upozornění C4615 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4615
dev_langs: C++
helpviewer_keywords: C4615
ms.assetid: 7b107c01-0da2-4e01-8b40-93813e30b94c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0541ea09fedf3c716bf970531735eafaecc048f6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4615"></a>C4615 kompilátoru upozornění (úroveň 1)
\#– Direktiva pragma upozornění: Neznámé uživatelské typ upozornění  
  
 Byl použit neplatný specifikátor upozornění s **– Direktiva pragma** [upozornění](../../preprocessor/warning.md). Chcete-li vyřešit chyby, použijte platný specifikátor upozornění.  
  
 Následující ukázka generuje C4615:  
  
```  
// C4615.cpp  
// compile with: /W1 /LD  
#pragma warning(enable : 4401)   // C4615, 'enable' not valid specifier  
  
// use the code below to resolve the error  
// #pragma warning(default : 4401)  
```