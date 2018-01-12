---
title: "Kompilátoru (úroveň 4) upozornění C4623 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4623
dev_langs: C++
helpviewer_keywords: C4623
ms.assetid: e630d8d0-f6ea-469c-a74f-07b027587225
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d9a47f0cc967011465286329461abc72eccb8c80
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4623"></a>C4623 kompilátoru upozornění (úroveň 4)
'`derived class`': výchozí konstruktor byl implicitně definován jako odstranit, protože základní třída výchozí konstruktor je nedostupný, nebo odstraněné  
  
 Konstruktor nebyl k dispozici v základní třídě a nebyl vygenerované odvozené třídy. Chyba kompilátoru způsobí, že pokusy o vytvoření tohoto typu objektu v zásobníku.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4623.  
  
```  
// C4623.cpp  
// compile with: /W4  
#pragma warning(default : 4623)  
class B {  
   B();  
};  
  
class C {  
public:  
   C();  
};  
  
class D : public B {};   // C4623 - to fix, make B's constructor public  
class E : public C {};   // OK - class C constructor is public  
  
int main() {  
   // D d;  will cause an error  
}  
```