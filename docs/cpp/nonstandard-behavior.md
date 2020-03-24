---
title: Nestandardní chování
ms.date: 05/06/2019
helpviewer_keywords:
- compatibility and compliance, nonstandard behavior
- Microsoft-specific, compiler behavior
- nonstandard behavior, compliance and compatibility
ms.assetid: a57dea27-dc79-4f64-8a83-017e84841773
ms.openlocfilehash: d3bb4ca843833cfe9e027f694f25c989895487bb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161032"
---
# <a name="nonstandard-behavior"></a>Nestandardní chování

V následujících oddílech jsou uvedeny některé z míst, kde implementace od C++ společnosti Microsoft nedodržuje C++ Standard. Čísla oddílů, která jsou uvedena níže, odkazují na čísla oddílů ve standardu C++ (ISO/IEC 14882:2011(E)).

Seznam omezení kompilátoru, která se liší od definic definovaných ve C++ standardu, je uveden v [omezeních kompilátoru](../cpp/compiler-limits.md).

## <a name="covariant-return-types"></a>Kovariantní návratové typy

Virtuální základní třídy nejsou podporovány jako kovariantní návratové typy, pokud virtuální funkce má proměnný počet argumentů. To není v souladu s oddílem 10.3, odstavcem 7 specifikace C++ ISO. Následující ukázka není zkompilována, čímž se [C2688](../error-messages/compiler-errors-2/compiler-error-c2688.md) Chyba kompilátoru.

```cpp
// CovariantReturn.cpp
class A
{
   virtual A* f(int c, ...);   // remove ...
};

class B : virtual A
{
   B* f(int c, ...);   // C2688 remove ...
};
```

## <a name="binding-nondependent-names-in-templates"></a>Názvy nezávislé vazby v šablonách

Kompilátor společnosti C++ Microsoft v současné době při prvotní analýze šablony nepodporuje názvy nezávisle na vazbě. To není v souladu s oddílem 14.6.3 specifikace C++ ISO. To může způsobit přetížení deklarované poté, co má být šablona (ale předtím, než je vytvořena instance šablony) zobrazena.

```cpp
#include <iostream>
using namespace std;

namespace N {
   void f(int) { cout << "f(int)" << endl;}
}

template <class T> void g(T) {
    N::f('a');   // calls f(char), should call f(int)
}

namespace N {
    void f(char) { cout << "f(char)" << endl;}
}

int main() {
    g('c');
}
// Output: f(char)
```

## <a name="function-exception-specifiers"></a>Specifikátory výjimek funkcí

Specifikátory výjimek funkcí jiné než `throw()` jsou analyzovány, ale nepoužívají se. To není v souladu s oddílem 15.4 specifikace ISO C++. Příklad:

```cpp
void f() throw(int); // parsed but not used
void g() throw();    // parsed and used
```

Další informace o specifikacích výjimek naleznete v tématu [Specifikace výjimek](../cpp/exception-specifications-throw-cpp.md).

## <a name="char_traitseof"></a>char_traits::eof()

C++ Standardní stavy, které [char_traits:: EOF](../standard-library/char-traits-struct.md#eof) nesmí odpovídat platnému `char_type` hodnotě. Kompilátor Microsoft C++ toto omezení vynutil pro typ **char**, ale ne pro typ **wchar_t**. To není v souladu s požadavky tabulky 62 v oddíle 12.1.1 specifikace C++ ISO. To zachycuje níže uvedený příklad.

```cpp
#include <iostream>

int main()
{
    using namespace std;

    char_traits<char>::int_type int2 = char_traits<char>::eof();
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;

    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;
}
```

## <a name="storage-location-of-objects"></a>Umístění úložiště objektů

Standard C++ (odstavec 6 oddílu 1.8) vyžaduje jedinečná umístění úložiště objektů jazyka C++. Nicméně u společnosti C++Microsoft existují případy, kdy typy bez datových členů budou sdílet umístění úložiště s jinými typy pro dobu života objektu.
