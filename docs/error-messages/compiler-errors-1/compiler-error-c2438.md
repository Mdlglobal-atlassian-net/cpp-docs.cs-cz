---
title: "C2438 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2438
dev_langs: C++
helpviewer_keywords: C2438
ms.assetid: 3a0ab3ba-d0e4-4d8f-971d-e503397cc827
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1771d3c6c241db6430eaa66fece5562a3bc1349a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2438"></a>C2438 chyby kompilátoru
"identifikátor": Nelze inicializovat statická třída dat přes – konstruktor  
  
 Konstruktor se používá k chybě při inicializaci je statický člen třídy. Statické členy musí být inicializován v definici mimo deklaraci třídy.  
  
 Následující ukázka generuje C2438:  
  
```  
// C2438.cpp  
struct X {  
   X(int i) : j(i) {}   // C2438  
   static int j;  
};  
  
int X::j;  
  
int main() {  
   X::j = 1;  
}  
```