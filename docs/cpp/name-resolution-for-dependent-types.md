---
title: Rozlišení názvů u závislých typů
ms.date: 11/04/2016
ms.assetid: 34066bb4-0c79-4fd8-bda7-539a60a277ab
ms.openlocfilehash: e9954eab2793f9adf0de75775563df0ae6f063f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161150"
---
# <a name="name-resolution-for-dependent-types"></a>Rozlišení názvů u závislých typů

Použijte **TypeName** pro kvalifikované názvy v definicích šablon a sdělte tak kompilátoru, že daný kvalifikovaný název identifikuje typ. Další informace naleznete v tématu [TypeName](../cpp/typename.md).

```cpp
// template_name_resolution1.cpp
#include <stdio.h>
template <class T> class X
{
public:
   void f(typename T::myType* mt) {}
};

class Yarg
{
public:
   struct myType { };
};

int main()
{
   X<Yarg> x;
   x.f(new Yarg::myType());
   printf("Name resolved by using typename keyword.");
}
```

```Output
Name resolved by using typename keyword.
```

Vyhledávání názvů pro závislé názvy prověřuje názvy z kontextu definice šablony – v následujícím příkladu by tento kontext byl `myFunction(char)`– a kontext instance šablony. V následujícím příkladu je vytvořena instance šablony v Main; Proto je `MyNamespace::myFunction` viditelná z bodu vytváření instancí a je vyzvednuta jako lepší shoda. Pokud by byla funkce `MyNamespace::myFunction` přejmenována, došlo by k zavolání funkce `myFunction(char)`.

Všechny názvy jsou vyhodnoceny jako závislé názvy. Přesto je doporučeno používat plně kvalifikované názvy, může-li dojít k jakýmkoli konfliktům.

```cpp
// template_name_resolution2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

void myFunction(char)
{
   cout << "Char myFunction" << endl;
}

template <class T> class Class1
{
public:
   Class1(T i)
   {
      // If replaced with myFunction(1), myFunction(char)
      // will be called
      myFunction(i);
}
};

namespace MyNamespace
{
   void myFunction(int)
   {
      cout << "Int MyNamespace::myFunction" << endl;
   }
};

using namespace MyNamespace;

int main()
{
   Class1<int>* c1 = new Class1<int>(100);
}
```

### <a name="output"></a>Výstup

```Output
Int MyNamespace::myFunction
```

### <a name="template-disambiguation"></a>Odstraňování mnohoznačnosti šablon

Visual Studio 2012 vynutil standardní pravidla C++ 98/03/11 pro nejednoznačnost pomocí klíčového slova Template. V následujícím příkladu bude Visual Studio 2010 akceptovat řádky, které nedodržují podmínky, i řádky pro vyhovující.  Visual Studio 2012 přijímá pouze vyhovující řádky.

```cpp
#include <iostream>
#include <ostream>
#include <typeinfo>
using namespace std;

template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    #if defined(NONCONFORMANT)
        typedef typename AY::Rebind<X>::Other AX; // nonconformant
    #elif defined(CONFORMANT)
        typedef typename AY::template Rebind<X>::Other AX; // conformant
    #else
        #error Define NONCONFORMANT or CONFORMANT.
    #endif
};

int main() {
    cout << typeid(Container<int, Allocator<float>>::AX).name() << endl;
}
```

Shoda s pravidly odstraňování mnohoznačnosti je požadována, protože jazyk C++ standardně předpokládá, že typ `AY::Rebind` není šablona, proto kompilátor interpretuje následující znak „`<`“ jako znak „menší než“. Pro správnou analýzu znaku „`Rebind`“ jako ostré závorky musí kompilátor vědět, že typ `<` je šablona.

## <a name="see-also"></a>Viz také

[Překlad názvů](../cpp/templates-and-name-resolution.md)
