---
title: Kompilátoru (úroveň 3) upozornění C4646 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4646
dev_langs:
- C++
helpviewer_keywords:
- C4646
ms.assetid: 23677e8e-603e-40e0-b99a-2e4894a1278e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36ff770877333042319b2a91dc5006e2ceb4118f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4646"></a>C4646 kompilátoru upozornění (úroveň 3)
funkce deklarovat s __declspec(noreturn) má návratový typ není void  
  
 Funkce označené jako [noreturn](../../cpp/noreturn.md) `__declspec` modifikátor by měl mít [void](../../cpp/void-cpp.md) návratovým typem.  
  
 Následující ukázka generuje C4646:  
  
```  
// C4646.cpp  
// compile with: /W3 /WX  
int __declspec(noreturn) TestFunction()  
{   // C4646  make return type void  
}  
```