---
title: "Kompilátoru (úroveň 4) upozornění C4625 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4625
dev_langs: C++
helpviewer_keywords: C4625
ms.assetid: 4cc99e50-846c-4784-97da-48b977067851
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c4b1cc20ea5f2ef03b2f2ebefa7a4b2c373d796f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4625"></a>C4625 kompilátoru upozornění (úroveň 4)
odvozené třídy': kopírovacího konstruktoru byl implicitně definován jako odstranit, protože základní třída kopírovacího konstruktoru je nedostupný, nebo odstraněné  
  
 Kopírovací konstruktor byl odstraněný nebo není k dispozici v základní třídě a nebyl proto vygenerované odvozené třídy. Chyba kompilátoru způsobí, že pokusy o kopírovat objekt tohoto typu.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4625 a ukazuje, jak ji odstranit.  
  
```  
// C4625.cpp  
// compile with: /W4 /c  
#pragma warning(default : 4625)  
  
struct A {  
   A() {}  
  
private:  
   A(const A&) {}  
};  
  
struct C : private virtual A {};  
struct B :  C {};   // C4625 no copy constructor  
  
struct D : A {};  
struct E :  D {};   // OK  
```