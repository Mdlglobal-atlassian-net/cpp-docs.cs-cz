---
title: Kompilátoru (úroveň 4) upozornění C4932 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4932
dev_langs:
- C++
helpviewer_keywords:
- C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d99fc58f9e6208db9aaeb8689e8be8b49f9aaea4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294112"
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