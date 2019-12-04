---
title: Chyba kompilátoru C2059
ms.date: 03/26/2019
f1_keywords:
- C2059
helpviewer_keywords:
- C2059
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
ms.openlocfilehash: 1d51d4c7873d43a655dc11fa8e0fa297b8a69bff
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735941"
---
# <a name="compiler-error-c2059"></a>Chyba kompilátoru C2059

Chyba syntaxe: token

Token způsobil chybu syntaxe.

Následující příklad vygeneruje chybovou zprávu pro řádek, který deklaruje `j`.

```cpp
// C2059e.cpp
// compile with: /c
// C2143 expected
// Error caused by the incorrect use of '*'.
   int j*; // C2059
```

Chcete-li zjistit příčinu chyby, zkontrolujte nejen řádek, který je uvedený v chybové zprávě, ale také řádky nad ním. Pokud prozkoumání řádků nevrátí žádné informace o problému, zkuste komentovat řádek uvedený v chybové zprávě a možná několik řádků nad ním.

Pokud se chybová zpráva vyskytne na symbolu, který následuje za `typedef` proměnnou, ujistěte se, že je proměnná definována ve zdrojovém kódu.

C2059 je vyvolána, když je název symbolu preprocesoru znovu použit jako identifikátor. V následujícím příkladu se kompilátor uvidí `DIGITS.ONE` jako číslo 1, které není platné jako název elementu výčtu:

```cpp
#define ONE 1

enum class DIGITS {
    ZERO,
    ONE // error C2059
};
```

Můžete získat C2059, jestli se symbol nevyhodnotí jako Nothing, jak může nastat, když se k zkompilování použije **/d**_symbol_ **=** .

```cpp
// C2059a.cpp
// compile with: /DTEST=
#include <stdio.h>

int main() {
   #ifdef TEST
      printf_s("\nTEST defined %d", TEST);   // C2059
   #else
      printf_s("\nTEST not defined");
   #endif
}
```

Další případ, ve kterém může C2059 nastat, je při kompilaci aplikace, která určuje strukturu ve výchozích argumentech funkce. Výchozí hodnota argumentu musí být výraz. Seznam inicializátorů – například jeden, který se používá k inicializaci struktury – není výraz.  Chcete-li tento problém vyřešit, definujte konstruktor, který provede požadovanou inicializaci.

Následující příklad generuje C2059:

```cpp
// C2059b.cpp
// compile with: /c
struct ag_type {
   int a;
   float b;
   // Uncomment the following line to resolve.
   // ag_type(int aa, float bb) : a(aa), b(bb) {}
};

void func(ag_type arg = {5, 7.0});   // C2059
void func(ag_type arg = ag_type(5, 7.0));   // OK
```

C2059 se může vyskytnout pro přetypování ve špatném formátu.

Následující ukázka generuje C2059:

```cpp
// C2059c.cpp
// compile with: /clr
using namespace System;
ref class From {};
ref class To : public From {};

int main() {
   From^ refbase = gcnew To();
   To^ refTo = safe_cast<To^>(From^);   // C2059
   To^ refTo2 = safe_cast<To^>(refbase);   // OK
}
```

K C2059 může dojít také v případě, že se pokusíte vytvořit název oboru názvů, který obsahuje tečku.

Následující ukázka generuje C2059:

```cpp
// C2059d.cpp
// compile with: /c
namespace A.B {}   // C2059

// OK
namespace A  {
   namespace B {}
}
```

K C2059 může docházet, když operátor, který může kvalifikovat název (`::`, `->`a `.`), musí následovat `template`klíčového slova, jak je znázorněno v následujícím příkladu:

```cpp
template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    typedef typename AY::Rebind<X>::Other AX; // error C2059
};
```

Ve výchozím nastavení C++ předpokládá, že `AY::Rebind` není šablonou. Proto následující `<` je interpretována jako znak menší než.  Kompilátor musíte výslovně říct, že `Rebind` je šablona, aby mohla správně analyzovat lomenou závorku. Chcete-li tuto chybu opravit, použijte klíčové slovo `template` v názvu závislého typu, jak je znázorněno zde:

```cpp
template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    typedef typename AY::template Rebind<X>::Other AX; // correct
};
```
