---
title: "C2273 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2273
dev_langs: C++
helpviewer_keywords: C2273
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 58f7f13303b9941cf07e90685d68d7114213ea2d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2273"></a>C2273 chyby kompilátoru
'type': Neplatný jako pravé straně operátoru '->.  
  
 Typ se zobrazí jako pravý operand `->` operátor.  
  
 Tato chyba může být způsobeno pokusu o přístup k uživatelsky definovaný typ. převod. Použití klíčového slova `operator` mezi -> a `type`.  
  
 Následující ukázka generuje C2273:  
  
```  
// C2273.cpp  
struct MyClass {  
   operator int() {  
      return 0;  
   }  
};  
int main() {  
   MyClass * ClassPtr = new MyClass;  
   int i = ClassPtr->int();   // C2273  
   int j = ClassPtr-> operator int();   // OK  
}  
```