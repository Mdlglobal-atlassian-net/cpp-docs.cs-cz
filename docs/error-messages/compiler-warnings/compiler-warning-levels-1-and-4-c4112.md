---
title: "C4112 kompilátoru upozornění (úrovně 1 a 4) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4112
dev_langs: C++
helpviewer_keywords: C4112
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 868411c2cef9ef6b984e95b5f5c6abaebd8ff91a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-levels-1-and-4-c4112"></a>C4112 kompilátoru upozornění (úrovně 1 a 4)
\#vyžaduje celé číslo mezi 1 a číslo řádku  
  
 [#Line](../../preprocessor/hash-line-directive-c-cpp.md) – direktiva určuje celočíselný parametr, který je mimo povolený rozsah.  
  
 Pokud zadaný parametr je menší než 1, čítač řádku se resetuje na hodnotu 1. Pokud zadaný parametr je větší než *číslo*, který je definován kompilátoru limit, řádku čítače se nemění. Toto je upozornění úrovně 1 v části kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) a úroveň 4 upozornění s rozšíření Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).  
  
 Následující ukázka generuje C4112:  
  
```  
// C4112.cpp  
// compile with: /W4  
#line 0   // C4112, value must be between 1 and number  
  
int main() {  
}  
```