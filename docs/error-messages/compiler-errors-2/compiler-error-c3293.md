---
title: Chyba kompilátoru C3293
ms.date: 07/21/2017
f1_keywords:
- C3293
helpviewer_keywords:
- C3293
ms.assetid: b772cf98-52e0-4e24-be23-1f5d87d999ac
ms.openlocfilehash: 1713632d21ef401fb1177350c81a4a64ed0503ec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760111"
---
# <a name="compiler-error-c3293"></a>Chyba kompilátoru C3293

přístupového objektu: pro přístup k výchozí vlastnosti (indexer) pro třídu Type použijte default.

K indexované vlastnosti došlo nesprávně.  Další informace naleznete v tématu [How to C++: use Properties in/CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md) .

**Visual studio 2017 a novější**: v nástroji visual Studio 2015 a starších verzích kompilátor v některých případech chybně identifikoval výchozí vlastnost jako výchozí indexer. Pro přístup k vlastnosti bylo možné problém vyřešit pomocí identifikátoru "výchozí". Alternativní řešení se jako klíčové slovo v C++ 11 stalo problematickým po zavedení výchozího nastavení. Proto v aplikaci Visual Studio 2017 byly opraveny chyby, které vyžadovaly alternativní řešení, a kompilátor nyní vyvolá chybu, pokud se pro přístup k výchozí vlastnosti třídy používá výchozí hodnota.

## <a name="example"></a>Příklad

Následující ukázka generuje C3293 v aplikaci Visual Studio 2015 a starší.

```cpp
// C3293.cpp
// compile with: /clr /c
using namespace System;
ref class IndexerClass {
public:
   // default indexer
   property int default[int] {
      int get(int index) { return 0; }
      void set(int index, int value) {}
   }
};

int main() {
   IndexerClass ^ ic = gcnew IndexerClass;
   ic->Item[0] = 21;   // C3293 in VS2015 OK in VS2017
   ic->default[0] = 21;   // OK in VS2015 and earlier

   String ^s = "Hello";
   wchar_t wc = s->Chars[0];   // C3293 in VS2015 OK in VS2017
   wchar_t wc2 = s->default[0];   // OK in VS2015 and earlier
   Console::WriteLine(wc2);
}
```
