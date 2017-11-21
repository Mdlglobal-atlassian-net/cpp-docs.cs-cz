---
title: "C2362 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2362
dev_langs: C++
helpviewer_keywords: C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e3a921084d696e6cf7abebc75d02d403cbcda2be
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2362"></a>C2362 chyby kompilátoru
Inicializace "identifikátor" bylo přeskočeno, goto popiskem.  
  
 Při kompilaci s [/Za](../../build/reference/za-ze-disable-language-extensions.md), přechodu na návěští zabrání inicializaci identifikátor.  
  
 Nelze přejít po deklaraci s inicializátoru Pokud deklaraci je uzavřené v bloku, která není zadaný, nebo proměnnou již byl inicializován.  
  
 Následující ukázka generuje C2326:  
  
```  
// C2362.cpp  
// compile with: /Za  
int main() {  
   goto label1;  
   int i = 1;      // C2362, initialization skipped  
label1:;  
}  
```  
  
 Možná řešení:  
  
```  
// C2362b.cpp  
// compile with: /Za  
int main() {  
   goto label1;  
   {  
      int j = 1;   // OK, this block is never entered  
   }  
label1:;  
}  
```