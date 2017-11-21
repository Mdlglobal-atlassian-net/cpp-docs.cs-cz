---
title: "C2677 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2677
dev_langs: C++
helpviewer_keywords: C2677
ms.assetid: 76bc0b65-f52a-45a6-b6d6-0555f89da9a8
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4362fdb85c6700c9f9592b9bbf626738e6c4d4b5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2677"></a>C2677 chyby kompilátoru
binární 'operátor': žádné globální operátor nalezen, což trvá typu "typ" (nebo není žádný převod přijatelné)  
  
 Chcete-li operátor použít, je třeba jej přetížit pro daný typ nebo definovat převod na typ, pro který je operátor definován.  
  
 Následující ukázka generuje C2677:  
  
```  
// C2677.cpp  
class C {  
public:  
   C(){}  
} c;  
  
class D {  
public:  
   D(){}  
   operator int(){return 0;}  
} d;  
  
int main() {  
   int i = 1 >> c;   // C2677  
   int j = 1 >> d;   // OK operator int() defined  
}  
```