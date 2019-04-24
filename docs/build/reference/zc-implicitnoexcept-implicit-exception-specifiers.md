---
title: /Zc:implicitNoexcept (specifikátory implicitních výjimek)
ms.date: 03/06/2018
f1_keywords:
- /Zc:implicitNoexcept
helpviewer_keywords:
- /Zc:implicitNoexcept
- Zc:implicitNoexcept
- -Zc:implicitNoexcept
ms.assetid: 71807652-6f9d-436b-899e-f52daa6f500b
ms.openlocfilehash: ec2b8c8fb4c7730a78c4403606d6fa61c0ddc374
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315557"
---
# <a name="zcimplicitnoexcept-implicit-exception-specifiers"></a>/Zc:implicitNoexcept (specifikátory implicitních výjimek)

Když **/Zc: implicitnoexcept** je zadána možnost, že kompilátor přidává implicitní [noexcept](../../cpp/noexcept-cpp.md) specifikátor výjimky definované kompilátorem zvláštní členské funkce a destruktory a deallocators. Ve výchozím nastavení **/Zc: implicitnoexcept** je tak, aby odpovídal ISO C ++ 11 standard povoleno. Zapnutí této možnosti zakáže implicitní `noexcept` na destruktory a dealloacators a speciální členské funkce definované kompilátoru.

## <a name="syntax"></a>Syntaxe

> **/Zc:implicitNoexcept**[**-**]

## <a name="remarks"></a>Poznámky

**/ Zc: implicitnoexcept** instruuje kompilátor, aby pomocí postupu v části 15.4 ISO standardu C ++ 11. Implicitně přidá `noexcept` výjimka specifikátor každý deklarován implicitně nebo explicitně přednastavené zvláštní členské funkce – výchozí konstruktor kopírování, konstruktor, konstruktor přesunutí, destruktor, operátor přiřazení kopie nebo přesunutí přiřazení operátor – a každá uživatelem definovaný destruktor nebo dealokátor funkce. Uživatelem definované dealokátor má implicitní `noexcept(true)` specifikátor výjimky. Pro destruktory definované uživatelem, je specifikátor implicitní výjimka `noexcept(true)` Pokud třída obsaženého člena nebo základní třída má destruktor, který není `noexcept(true)`. Pro kompilátorem generované zvláštní členské funkce, pokud žádné funkce přímo vyvolávat tato funkce je v podstatě `noexcept(false)`, je specifikátor implicitní výjimka `noexcept(false)`. V opačném případě je specifikátor implicitní výjimka `noexcept(true)`.

Kompilátor negeneruje specifikátor implicitní výjimky pro funkce deklarované s použitím explicitní `noexcept` nebo `throw` specifikátory nebo `__declspec(nothrow)` atribut.

Ve výchozím nastavení **/Zc: implicitnoexcept** je povolená. [/ Permissive-](permissive-standards-conformance.md) nemá vliv na možnost **/Zc: implicitnoexcept**.

Pokud tato možnost je vypnuta zadáním **/Zc:implicitNoexcept-**, žádné specifikátory implicitních výjimek jsou generovány kompilátorem. Toto chování je stejné jako Visual Studio 2013, pokud by mohla mít destruktory a deallocators, u kterých nebylo specifikátory výjimek `throw` příkazy. Ve výchozím nastavení a kdy **/Zc: implicitnoexcept** není zadán, pokud `throw` příkaz dochází za běhu ve funkci s implicitní `noexcept(true)` specifikátor, způsobí, že okamžité vyvolání `std::terminate`, a Normální odvíjení chování pro obslužné rutiny výjimek není zaručena. K identifikaci této situaci, kompilátor generuje [upozornění kompilátoru (úroveň 1) C4297](../../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md). Pokud `throw` je úmyslné, doporučujeme změnit váš deklarace funkce mít explicitní `noexcept(false)` specifikátor namísto použití **/Zc:implicitNoexcept-**.

Tato ukázka předvádí, jak uživatelem definovaný destruktor, který nemá žádné explicitní výjimky specifikátor chová, když **/Zc: implicitnoexcept** možností je nastavit nebo zakázáno. Chcete-li zobrazit chování při nastavení, kompilovat s použitím `cl /EHsc /W4 implicitNoexcept.cpp`. Chcete-li zobrazit chování, pokud je zakázán, kompilovat s použitím `cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp`.

```cpp
// implicitNoexcept.cpp
// Compile by using: cl /EHsc /W4 implicitNoexcept.cpp
// Compile by using: cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp

#include <iostream>
#include <cstdlib>      // for std::exit, EXIT_FAILURE, EXIT_SUCCESS
#include <exception>    // for std::set_terminate

void my_terminate()
{
    std::cout << "Unexpected throw caused std::terminate" << std::endl;
    std::cout << "Exit returning EXIT_FAILURE" << std::endl;
    std::exit(EXIT_FAILURE);
}

struct A {
    // Explicit noexcept overrides implicit exception specification
    ~A() noexcept(false) {
        throw 1;
    }
};

struct B : public A {
    // Compiler-generated ~B() definition inherits noexcept(false)
    ~B() = default;
};

struct C {
    // By default, the compiler generates an implicit noexcept(true)
    // specifier for this user-defined destructor. To enable it to
    // throw an exception, use an explicit noexcept(false) specifier,
    // or compile by using /Zc:implicitNoexcept-
    ~C() {
        throw 1; // C4297, calls std::terminate() at run time
    }
};

struct D : public C {
    // This destructor gets the implicit specifier of its base.
    ~D() = default;
};

int main()
{
    std::set_terminate(my_terminate);

    try
    {
        {
            B b;
        }
    }
    catch (...)
    {
        // exception should reach here in all cases
        std::cout << "~B Exception caught" << std::endl;
    }
    try
    {
        {
            D d;
        }
    }
    catch (...)
    {
        // exception should not reach here if /Zc:implicitNoexcept
        std::cout << "~D Exception caught" << std::endl;
    }
    std::cout << "Exit returning EXIT_SUCCESS" << std::endl;
    return EXIT_SUCCESS;
}
```

Při kompilaci pomocí výchozí nastavení **/Zc: implicitnoexcept**, ukázka generuje tento výstup:

```Output
~B Exception caught
Unexpected throw caused std::terminate
Exit returning EXIT_FAILURE
```

Při kompilaci pomocí nastavení **/Zc:implicitNoexcept-**, ukázka generuje tento výstup:

```Output
~B Exception caught
~D Exception caught
Exit returning EXIT_SUCCESS
```

Další informace o problémech přizpůsobení v aplikaci Visual C++, naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala **/Zc: implicitnoexcept** nebo **/Zc:implicitNoexcept-** a klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](zc-conformance.md)<br/>
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[Specifikace výjimek (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[ukončit](../../standard-library/exception-functions.md#terminate)<br/>
