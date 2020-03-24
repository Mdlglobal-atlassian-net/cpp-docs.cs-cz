---
title: Upozornění kompilátoru (úroveň 1) C4342
ms.date: 11/04/2016
f1_keywords:
- C4342
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
ms.openlocfilehash: 8ac00d3d57f8cf7d6c85f3106dbe9b8c3cb9adf0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162917"
---
# <a name="compiler-warning-level-1-c4342"></a>Upozornění kompilátoru (úroveň 1) C4342

Změna chování: byla volána*funkce Function*, ale v předchozích verzích byl volán operátor member.

Ve verzích vizuálu C++ před visual Studio 2002 byl volán člen, ale toto chování bylo změněno a kompilátor nyní vyhledá nejlepší shodu v oboru názvů.

Pokud byl nalezen operátor členu, kompilátor předtím nebral žádné operátory oboru názvů. Pokud je v oboru názvů lepší shoda, aktuální kompilátor je správně volá, zatímco předchozí kompilátory to nepovažují.

Toto upozornění by mělo být zakázáno po úspěšném přenosu kódu do aktuální verze.  Kompilátor může poskytnout falešně pozitivní výsledky, což vygeneruje toto upozornění pro kód, u kterého nedochází ke změně chování.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

Následující ukázka generuje C4342:

```cpp
// C4342.cpp
// compile with: /EHsc /W1
#include <fstream>
#pragma warning(default: 4342)
using namespace std;
struct X : public ofstream {
   X();
};

X::X() {
   open( "ofs_bug_ev.txt." );
   if ( is_open() ) {
      *this << "Text" << "<-should be text" << endl;   // C4342
      *this << ' ' << "<-should be space symbol" << endl;   // C4342
   }
}

int main() {
   X b;
   b << "Text" << "<-should be text" << endl;
   b << ' ' << "<-should be space symbol" << endl;
}
```
