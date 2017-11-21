---
title: "Kompilátoru (úroveň 4) upozornění C4242 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4242
dev_langs: C++
helpviewer_keywords: C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b0e51952a615037b4df3a43fb37cd4f3dc3e717e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4242"></a>Kompilátoru (úroveň 4) upozornění C4242
"identifikátor": převod 'type1' na 'type2', možné ztrátě dat.  
  
 Typy se liší. Převod typů může dojít ke ztrátě dat. Kompilátor umožňuje převod typů.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
 Další informace o C4242 v tématu [běžné chyby kompilátoru](http://msdn.microsoft.com/library/windows/desktop/aa384160).  
  
 Následující ukázka generuje C4242:  
  
```  
// C4242.cpp  
// compile with: /W4  
#pragma warning(4:4242)  
int func() {  
   return 0;  
}  
  
int main() {  
   char a;  
   a = func();   // C4242, return type and variable type do not match  
}  
```