---
title: "Kompilátoru (úroveň 4) upozornění C4932 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4932
dev_langs: C++
helpviewer_keywords: C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9f6370e4f8445900ba021c043ece71f9e61f9c8f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4932"></a>C4932 kompilátoru upozornění (úroveň 4)
__identifier(Identifier) a \_jsou _identifier(identifier)  
  
 Kompilátor není schopen rozlišit mezi **_finally** a `__finally` nebo `__try` a **_try** jako parametr předaný [__identifier](../../windows/identifier-cpp-cli.md). Byste neměli používat obě jako identifikátory v stejný program jako povede to [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) chyba.  
  
 Následující ukázka generuje C4932:  
  
```  
// C4932.cpp  
// compile with: /clr /W4 /WX  
int main() {  
   int __identifier(_finally) = 245;   // C4932  
   int __identifier(__finally) = 25;   // C4932  
}  
```