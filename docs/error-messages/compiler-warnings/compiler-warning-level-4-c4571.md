---
title: "Kompilátoru (úroveň 4) upozornění C4571 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4571
dev_langs:
- C++
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cab2068b6117f092dcc098591bb620156b2c0cf6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4571"></a>C4571 kompilátoru upozornění (úroveň 4)
Informační: catch(...) sémantiku změněné od Visual C++ 7.1; strukturované výjimky (SEH) jsou již zachyceny  
  
 C4571 se vygeneruje pro každý catch(...) blok, když kompilujete s **/EHs**.  
  
 Při kompilaci s **/EHs**, nebude catch(...) blok catch strukturovaného výjimek (dělení nulou ukazatele null, např.), catch(...) bloku bude pouze catch explicitně vyvolání výjimky jazyka C++.  Další informace najdete v tématu [zpracování výjimek](../../cpp/exception-handling-in-visual-cpp.md).  
  
 Toto upozornění je ve výchozím nastavení vypnutý.  Zapnout tato upozornění na zajistit, aby při kompilaci s **/EHs** vaše bloků catch (...) nemáte v úmyslu zachytit strukturovaných výjimky.  V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
 C4571 můžete vyřešit jedním z následujících způsobů  
  
-   Kompilovat s **/EHa** Pokud stále chcete vaší catch(...) bloky zachytit strukturovaných výjimky.  
  
-   Nepovolujte C4571, pokud nechcete, aby vaše catch(...) bloky zachytit strukturovaných výjimky, ale nadále chcete používat catch(...) bloky.  Můžete stále catch strukturovaných výjimky používání strukturovaného zpracování klíčová slova výjimek (**__try**, **__except**, a **__finally**).  Ale pamatujte si, že při kompilaci **/EHs** destruktory bude volat pouze, pokud je vyvolána výjimka C++, ne v případě, že dojde k výjimce SEH.  
  
-   Blok catch(...) nahraďte bloků catch pro konkrétní výjimky jazyka C++ a volitelně přidejte strukturovaného zpracování kolem zpracování výjimek jazyka C++ výjimek (**__try**, **__except**, a **_ _finally**).  V tématu [strukturované zpracování výjimek (C/C++)](../../cpp/structured-exception-handling-c-cpp.md) Další informace.  
  
 V tématu [/EH (Model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4571.  
  
```  
// C4571.cpp  
// compile with: /EHs /W4 /c  
#pragma warning(default : 4571)  
int main() {  
   try {  
      int i = 0, j = 1;  
      j /= i;   // this will throw a SE (divide by zero)  
   }  
   catch(...) {}   // C4571 warning  
}  
```