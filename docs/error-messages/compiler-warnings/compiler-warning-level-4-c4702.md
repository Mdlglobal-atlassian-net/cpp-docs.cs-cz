---
title: Upozornění kompilátoru (úroveň 4) C4702
ms.date: 11/04/2016
f1_keywords:
- C4702
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
ms.openlocfilehash: 5e46bfef925f999ed7f04b5bbe7c88800209ed14
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990648"
---
# <a name="compiler-warning-level-4-c4702"></a>Upozornění kompilátoru (úroveň 4) C4702

nedosažitelný kód

Toto upozornění je výsledkem práce s vyhovujícími kompilátory, které byly provedeny pro sadu Visual Studio .NET 2003: nedosažitelný kód. Když kompilátor (back-end) zjistí nedosažitelný kód, vygeneruje C4702 upozornění úrovně 4.

Pro kód, který je platný v rámci Visual Studio .NET 2003 i Visual Studio .NET verze vizuálu C++, odeberte nedosažitelný kód nebo zajistěte, aby byl veškerý zdrojový kód dosažitelný pomocí nějakého toku provádění.

## <a name="example"></a>Příklad

Následující ukázka generuje C4702.

```cpp
// C4702.cpp
// compile with: /W4
#include <stdio.h>

int main() {
   return 1;
   printf_s("I won't print.\n");   // C4702 unreachable
}
```

## <a name="example"></a>Příklad

Při kompilaci s **/GX**, **/EHC**, **/EHsc**nebo **/EHAC** a pomocí externích funkcí jazyka c může být kód nedosažitelný, protože externí funkce jazyka c se předpokládá, že nejsou throw, takže blok catch není dosažitelný.  Pokud se domníváte, že toto upozornění není platné, protože funkce může vyvolat, kompilovat pomocí **/EHa** nebo **/EHS**, v závislosti na vyvolané výjimce.

Další informace naleznete v tématu [/EH (model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md) , kde najdete další informace.

Následující ukázka generuje C4702.

```cpp
// C4702b.cpp
// compile with: /W4 /EHsc
#include <iostream>

using namespace std;
extern "C" __declspec(dllexport) void Function2(){}

int main() {
   try {
      Function2();
   }
   catch (...) {
      cout << "Exp: Function2!" << endl;   // C4702
   }
}
```
