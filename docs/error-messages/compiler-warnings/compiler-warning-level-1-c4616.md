---
title: "Kompilátoru (úroveň 1) upozornění C4616 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4616
dev_langs: C++
helpviewer_keywords: C4616
ms.assetid: 71e15265-c5bc-42ce-a6a9-4879892472b1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 60e71e087757b105d910434ec4eef4e64740b9b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4616"></a>C4616 kompilátoru upozornění (úroveň 1)
\#– Direktiva pragma upozornění: upozornění číslo, číslo' není platný kompilátoru upozornění  
  
 Upozornění číslo zadané v [upozornění](../../preprocessor/warning.md) – Direktiva pragma nelze přiřadit. – Direktiva pragma byl ignorován.  
  
 Následující ukázka generuje C4616:  
  
```  
// C4616.cpp  
// compile with: /W1 /c  
#pragma warning( disable : 0 )   // C4616  
#pragma warning( disable : 999 )   // OK  
#pragma warning( disable : 4998 )   // OK  
```