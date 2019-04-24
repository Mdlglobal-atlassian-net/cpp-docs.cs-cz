---
title: Kompilátor upozornění (úroveň 1) C4342
ms.date: 11/04/2016
f1_keywords:
- C4342
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
ms.openlocfilehash: 439c4976f25688fd9220c3f58ceb933266b5f15c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187506"
---
# <a name="compiler-warning-level-1-c4342"></a>Kompilátor upozornění (úroveň 1) C4342

Změna chování: "*funkce*" volá se, ale operátor členu byl zavolán v předchozích verzích

Ve verzích Visual C++ před Visual Studio 2002 byla volána členem, ale toto chování nebylo změněno a kompilátor nyní vyhledá nejlepší shodu v oboru názvů.

Pokud operátor členu byl nalezen, kompilátor by dříve zvažte libovolný obor názvů operátory oboru. Pokud je lepší shodu v oboru názvů, aktuální kompilátor správně volá, že předchozí kompilátory by považujte jej.

Po úspěšném přeneste kód do aktuální verze je třeba zakázat toto upozornění.  Kompilátor může dát počet falešně pozitivních výsledků, generuje toto upozornění pro kód tam, kde není žádná změna chování.

Toto upozornění je vypnuto ve výchozím nastavení. Další informace najdete v tématu [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

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