---
title: Chyba kompilátoru C3293
ms.date: 07/21/2017
f1_keywords:
- C3293
helpviewer_keywords:
- C3293
ms.assetid: b772cf98-52e0-4e24-be23-1f5d87d999ac
ms.openlocfilehash: 84d539722474d5f5dfffe1f6fe121bb7349ba131
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548206"
---
# <a name="compiler-error-c3293"></a>Chyba kompilátoru C3293

"objekt": "default" používat pro přístup k výchozí vlastnost (indexer) pro třídu 'type'

Indexovaná vlastnost se použila správně.  Naleznete v tématu [postupy: používání vlastností v jazyce C + +/ CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md) Další informace.

**Visual Studio 2017 a novější**: V sadě Visual Studio 2015 a starší, kompilátor v některých případech misidentified výchozí vlastnost jako výchozí indexeru. Bylo možné tento problém obejít, pomocí identifikátor "Výchozí" pro přístup k vlastnosti. Alternativní řešení, samotný začal být problematické po výchozí byla zavedená jako klíčové slovo v C ++ 11. Proto v sadě Visual Studio 2017 které jsme opravili chyby, které vyžaduje řešení, a kompilátor vyvolá chybu nyní, když "Výchozí" se používá pro přístup k výchozí vlastnost pro třídu.

## <a name="example"></a>Příklad

Následující ukázka generuje C3293 v sadě Visual Studio 2015 a starší.

```
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