---
title: C2273 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2273
dev_langs:
- C++
helpviewer_keywords:
- C2273
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f49ee00ba5617b494e27650c38dad679ae6767a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170866"
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