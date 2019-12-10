---
title: Upozornění kompilátoru (úroveň 4) C4571
ms.date: 11/04/2016
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 3a8f2093e90f8a681d171e19e2b8a066546f8684
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990658"
---
# <a name="compiler-warning-level-4-c4571"></a>Upozornění kompilátoru (úroveň 4) C4571

informační: sémantika catch (...) se od verze C++ Visual 7,1 změnila. strukturované výjimky (SEH) už se nezachycují.

C4571 se generuje pro každý blok catch (...) při kompilování s **/EHS**.

Při kompilaci s **/EHS**nebude blok catch (...) zachytit strukturovanou výjimku (například nulou, null ukazatel, například); blok catch (...) bude zachytit jenom explicitně vygenerované, C++ výjimky.  Další informace naleznete v tématu [zpracování výjimek](../../cpp/exception-handling-in-visual-cpp.md).

Toto upozornění je ve výchozím nastavení vypnuté.  Toto upozornění zapněte, aby se zajistilo, že při kompilaci s **/EHS** vašich bloků catch (...) nechcete zachytit strukturované výjimky.  Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

C4571 můžete vyřešit jedním z následujících způsobů:

- Zkompilujte pomocí **/EHa** , pokud stále chcete, aby bloky catch (...) byly zachyceny strukturované výjimky.

- Nepovolujte C4571, pokud nechcete, aby vaše bloky catch (...) zachytily strukturované výjimky, ale přesto chcete použít bloky catch (...).  Strukturované výjimky můžete nadále zachytit pomocí klíčových slov strukturovaného zpracování výjimek ( **__try**, **__except**a **__finally**).  Nezapomeňte však, že zkompilované destruktory **/EHS** budou volány pouze v případě C++ , že dojde k výjimce, nikoli při výskytu výjimky SEH.

- Nahraďte blok catch (...) bloky catch pro konkrétní C++ výjimky a volitelně přidejte strukturované zpracování C++ výjimek kolem zpracování výjimek ( **__try**, **__except**a **__finally**).  Další informace naleznete v tématu [zpracování strukturovanéC++výjimky (C/)](../../cpp/structured-exception-handling-c-cpp.md) .

Další informace naleznete v tématu [/EH (model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C4571.

```cpp
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
