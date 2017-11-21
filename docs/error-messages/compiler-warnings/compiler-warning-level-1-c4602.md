---
title: "Kompilátoru (úroveň 1) upozornění C4602 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4602
dev_langs: C++
helpviewer_keywords: C4602
ms.assetid: c1f0300f-e2a2-4c9e-a7c3-4c7318d10509
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ddc73b06ef19b9b14e4cf4fd4cf54252d7629ff8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4602"></a>C4602 kompilátoru upozornění (úroveň 1)
\#pop_macro – Direktiva pragma: "makro název" žádné předchozí push_macro – #pragma tohoto identifikátoru  
  
 Pokud používáte [pop_macro –](../../preprocessor/pop-macro.md) pro konkrétní makro, musíte nejprve předané tento název makra pro [push_macro –](../../preprocessor/push-macro.md). Například následující ukázka generuje C4602:  
  
```  
// C4602.cpp  
// compile with: /W1  
int main()  
{  
   #pragma pop_macro("x")   // C4602 x is not on the stack  
}  
```