---
title: Compiler Error C2143
ms.date: 11/04/2016
f1_keywords:
- C2143
helpviewer_keywords:
- C2143
ms.assetid: 1d8d1456-e031-4965-9240-09a6e33ba81c
ms.openlocfilehash: ed4bc7eea85e5263d59817082caed99bde3d75d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353479"
---
# <a name="compiler-error-c2143"></a>Compiler Error C2143

Chyba syntaxe: chybí "token1" před "token2.

Kompilátor očekává konkrétní token (to znamená, že prvky jazyka jiné než prázdné znaky) a místo toho se našel jiný token.

Zkontrolujte, [referenční dokumentace jazyka C++](../../cpp/cpp-language-reference.md) k určení, kde je syntakticky nesprávný kód. Protože kompilátor může nahlásit tuto chybu, jakmile narazí na řádek, který způsobí, že problém, zkontrolujte několika řádky kódu, které před chybou.

C2143 může dojít v různých situacích.

To může nastat, když operátor, který se může kvalifikovat název (`::`, `->`, a `.`) musí následovat klíčové slovo `template`, jako v tomto příkladu:

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::PutFuncType<Ty, PropTy> // error C2143
    {
    };
};
```

Ve výchozím nastavení, C++, předpokládá, že `Ty::PutFuncType` není šablona; proto následující `<` je interpretován jako symbol méně – znaménko.  Je zapotřebí sdělit kompilátoru explicitně, který `PutFuncType` je šablona tak, aby se může správně analyzovat lomená závorka. Chcete-li opravit tuto chybu, použijte `template` – klíčové slovo pro název závislého typu, jak je znázorněno zde:

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct
    {
    };
};
```

C2143 může dojít, když **/CLR** se používá a `using` – direktiva obsahuje chybu syntaxe:

```cpp
// C2143a.cpp
// compile with: /clr /c
using namespace System.Reflection;   // C2143
using namespace System::Reflection;
```

Může dojít také při kompilaci zdrojového kódu pomocí syntaxe CLR bez použití také **/CLR**:

```cpp
// C2143b.cpp
ref struct A {   // C2143 error compile with /clr
   void Test() {}
};

int main() {
   A a;
   a.Test();
}
```

První neprázdný znak, který následuje `if` příkaz musí být levá závorka. Kompilátor nelze převést vše ostatní:

```cpp
// C2143c.cpp
int main() {
   int j = 0;

   // OK
   if (j < 25)
      ;

   if (j < 25)   // C2143
}
```

C2143 může dojít, když chybí pravé složené závorky, (otevírací) nebo středník na řádku, kde se zjistila chyba nebo na jeden z řádků přímo nad:

```cpp
// C2143d.cpp
// compile with: /c
class X {
   int member1;
   int member2   // C2143
} x;
```

Nebo pokud je neplatná značka v deklaraci třídy:

```cpp
// C2143e.cpp
class X {
   int member;
} x;

class + {};   // C2143 + is an invalid tag name
class ValidName {};   // OK
```

Nebo pokud popisek není připojen k příkazu. Pokud samostatně, je nutné umístit popisek, například na konci složeného příkazu, připojte ji k příkaz null:

```cpp
// C2143f.cpp
// compile with: /c
void func1() {
   // OK
   end1:
      ;

   end2:   // C2143
}
```

Této chybě může dojít, když typ ve standardní knihovně jazyka C++ je provedeno neúplného volání:

```cpp
// C2143g.cpp
// compile with: /EHsc /c
#include <vector>
static vector<char> bad;   // C2143
static std::vector<char> good;   // OK
```

Nebo nebyla nalezena `typename` – klíčové slovo:

```cpp
// C2143h.cpp
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};
template <typename T>
X<T>::Y X<T>::memFunc() {   // C2143
// try the following line instead
// typename X<T>::Y X<T>::memFunc() {
   return Y();
}
```

Nebo pokud se pokusíte definovat explicitní vytváření instancí:

```cpp
// C2143i.cpp
// compile with: /EHsc /c
// template definition
template <class T>
void PrintType(T i, T j) {}

template void PrintType(float i, float j){}   // C2143
template void PrintType(float i, float j);   // OK
```

V programu jazyka C proměnné musí být deklarovány na začátku funkce a nemohou být deklarovány po funkci spouští instrukce jiné deklarace.

```C
// C2143j.c
int main()
{
    int i = 0;
    i++;
    int j = 0; // C2143
}
```
