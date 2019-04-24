---
title: Kompilátor upozornění (úroveň 4) C4571
ms.date: 11/04/2016
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 92164bf297a44871897b6c6150eb54f8c5ccf3cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220452"
---
# <a name="compiler-warning-level-4-c4571"></a>Kompilátor upozornění (úroveň 4) C4571

Informační: sémantika catch(...) se od verze Visual C++ 7.1; změnila strukturované výjimky (SEH) už se nezachycují.

C4571 je vygenerována pro každý blok catch(...) při kompilaci s **/EHS**.

Při kompilaci s **/EHS**, blok catch(...) nezachytí strukturovaných výjimek (dělení nulou, ukazatel s hodnotou null, například); catch(...) bloku se pouze bloku catch explicitně vyvolána, výjimky jazyka C++.  Další informace najdete v tématu [zpracování výjimek](../../cpp/exception-handling-in-visual-cpp.md).

Toto upozornění je vypnuto ve výchozím nastavení.  Zapnout toto upozornění na k tomu, aby při kompilaci s **/EHS** vaše bloky catch (...) nemáte v úmyslu catch strukturované výjimky.  Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

V jednom z následujících způsobů, můžete vyřešit C4571

- Kompilovat s **/EHa** Pokud stále chcete, aby vaše catch(...) bloků catch strukturované výjimky.

- Nepovolujte C4571, pokud nechcete, aby vaše catch(...) bloků catch strukturované výjimky, ale chcete použít catch(...) bloky.  Je stále možné zachytit strukturované výjimky používání strukturovaného zpracování klíčová slova výjimek (**__try**, **__except**, a **__finally**).  Ale nezapomeňte, že při kompilaci **/EHS** destruktory bude volat pouze při vyvolání výjimky jazyka C++, ne v případě, že dojde k výjimce SEH.

- Nahraďte bloky catch pro konkrétní blok catch(...) C++ výjimky a volitelně přidat kolem zpracování strukturovaných výjimek C++ zpracování výjimek (**__try**, **__except**, a **__finally**).  Zobrazit [strukturovaného zpracování výjimek (C/C++)](../../cpp/structured-exception-handling-c-cpp.md) Další informace.

Zobrazit [/EH (Model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md) Další informace.

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