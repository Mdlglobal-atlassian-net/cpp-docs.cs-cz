---
title: "C2627 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2627
dev_langs: C++
helpviewer_keywords: C2627
ms.assetid: 7fc6c5ac-c7c9-4f0b-ad52-f52252526458
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2af1b475fb6eff2a37f333aa0ef5ed07eae791e2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2627"></a>C2627 chyby kompilátoru
'function': není povoleno v anonymní sjednocení – členská funkce  
  
 [Anonymní sjednocení](../../cpp/unions.md#anonymous_unions) nemůže mít členské funkce.  
  
 Následující ukázka generuje C2627:  
  
```  
// C2627.cpp  
int main() {  
   union { void f(){} };   // C2627  
   union X { void f(){} };  
}  
```