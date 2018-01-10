---
title: "Kompilátoru (úroveň 3) upozornění C4398 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4398
dev_langs: C++
helpviewer_keywords: C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d5ce6355e50c1ea2594820388edc34c69ea0e899
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4398"></a>C4398 kompilátoru upozornění (úroveň 3)
"proměnné": globální objektu na proces nemusí pracovat správně s více domén; Zvažte použití __declspec(appdomain)  
  
 Virtuální funkce s [__clrcall](../../cpp/clrcall.md) konvence volání v nativním typu způsobí, že vytvoření za vtable domény aplikace. Tuto proměnnou nemusí správně opravit, pokud se používá ve více doménách aplikace.  
  
 Toto upozornění můžete vyřešit explicitní označení proměnnou `__declspec(appdomain)`. Ve verzích sady Visual Studio před Visual Studio 2017, můžete vyřešit toto upozornění kompilujete s **/CLR: pure**, takže globální proměnné jednotlivé domény aplikace ve výchozím nastavení.  
  
 Další informace najdete v tématu [appdomain](../../cpp/appdomain.md) a [domény aplikace a jazyk Visual C++](../../dotnet/application-domains-and-visual-cpp.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4398.  
  
```  
// C4398.cpp  
// compile with: /clr /W3 /c  
struct S {  
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall  
};  
  
S glob_s;   // C4398  
__declspec(appdomain) S glob_s2;   // OK  
```