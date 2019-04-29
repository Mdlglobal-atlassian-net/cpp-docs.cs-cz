---
title: Chyba kompilátoru C2059
ms.date: 03/26/2019
f1_keywords:
- C2059
helpviewer_keywords:
- C2059
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
ms.openlocfilehash: 2fb2aa86a1fd8f8e0710d787682fdd44abd941ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408664"
---
# <a name="compiler-error-c2059"></a>Chyba kompilátoru C2059

syntax error : 'token'

Token, který způsobil chybu syntaxe.

Následující příklad vygeneruje chybovou zprávu pro řádek, který deklaruje `j`.

```
// C2059e.cpp
// compile with: /c
// C2143 expected
// Error caused by the incorrect use of '*'.
   int j*; // C2059
```

Pokud chcete zjistit příčinu chyby, zkontrolujte nejen řádku, který je uvedený v chybové zprávě, ale také řádcích nad ním. Pokud zkoumání řádky se vrací potuchy o problému, zkuste okomentováním řádku, který je uvedený v chybové zprávě a možná několika řádcích nad ním.

Pokud chybová zpráva se zobrazí v symbolu, který bezprostředně následuje po `typedef` proměnnou, ujistěte se, že je proměnná definovaná ve zdrojovém kódu.

C2059 se vyvolá, když název symbol preprocesoru je znovu použít jako identifikátor. V následujícím příkladu kompilátor narazí `DIGITS.ONE` jako číslo 1, což je neplatný jako název elementu výčtu:

```cpp
#define ONE 1

enum class DIGITS {
    ZERO,
    ONE // error C2059
};
```

Můžete obdržet C2059, pokud symbol vyhodnotí jako nothing, protože může dojít, když **/D**_symbol_ **=** se používá ke kompilaci.

```
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

Dalším užitečným, ve kterém může dojít C2059 je při kompilaci aplikace, která určuje strukturu ve výchozí argumenty pro funkci. Výchozí hodnota pro argument musí být výraz. Seznam inicializátorů – například takový, který používá k inicializaci strukturu – není výraz.  Chcete-li vyřešit tento problém, definujte konstruktor k provedení požadované inicializace.

Následující příklad generuje C2059:

```
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

C2059 může dojít přetypování chybně vytvořený.

Následující ukázka generuje C2059:

```
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

C2059 může vzniknout také při pokusu o vytvoření názvu oboru názvů, který obsahuje tečku.

Následující ukázka generuje C2059:

```
// C2059d.cpp
// compile with: /c
namespace A.B {}   // C2059

// OK
namespace A  {
   namespace B {}
}
```

C2059 může dojít, pokud operátor, který se může kvalifikovat název (`::`, `->`, a `.`) musí následovat klíčové slovo `template`, jak je znázorněno v tomto příkladu:

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

Ve výchozím nastavení, C++, předpokládá, že `AY::Rebind` není šablona; proto následující `<` je interpretován jako symbol méně – znaménko.  Je zapotřebí sdělit kompilátoru explicitně, který `Rebind` je šablona tak, aby se může správně analyzovat lomená závorka. Chcete-li opravit tuto chybu, použijte `template` – klíčové slovo pro název závislého typu, jak je znázorněno zde:

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
