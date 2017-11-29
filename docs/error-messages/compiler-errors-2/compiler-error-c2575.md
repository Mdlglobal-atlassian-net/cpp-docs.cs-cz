---
title: "C2575 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2575
dev_langs: C++
helpviewer_keywords: C2575
ms.assetid: 9eb45706-37ef-4481-b373-6d193ba13634
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 63e31d1cb3b6ebe7129510464732a37ae416da82
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2575"></a>C2575 chyby kompilátoru
"identifikátor": pouze členských funkcí a databáze, které mohou být virtuální  
  
 Globální funkce nebo třída je deklarovaná `virtual`. Toto není povoleno.  
  
 Následující ukázka generuje C2575:  
  
```  
// C2575.cpp  
// compile with: /c  
virtual void func() {}   // C2575  
  
void func2() {}  
struct A {  
   virtual void func2(){}  
};  
```