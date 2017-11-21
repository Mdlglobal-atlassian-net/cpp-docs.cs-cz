---
title: "C2679 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2679
dev_langs: C++
helpviewer_keywords: C2679
ms.assetid: 1a5f9d00-9190-4aa6-bc72-949f68ec136f
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7b2eb3e0e55442ad4525dea266d4f1ebc4f87039
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2679"></a>C2679 chyby kompilátoru
binární 'operátor': žádná operátorem najít, což trvá pravém operand typu "typ" (nebo není žádný převod přijatelné)  
  
 Chcete-li operátor použít, je třeba jej přetížit pro daný typ nebo definovat převod na typ, pro který je operátor definován.  
  
 Následující ukázka generuje C2679:  
  
```  
// C2679.cpp  
class C {  
public:  
   C();   // no constructor with an int argument  
} c;  
  
class D {  
public:  
   D(int) {}  
   D(){}  
} d;  
  
int main() {  
   c = 10;   // C2679  
   d = 10;   // OK  
}  
```