---
title: '/ Zc: implicitnoexcept (specifikátory implicitních výjimek) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:implicitNoexcept
dev_langs:
- C++
helpviewer_keywords:
- /Zc:implicitNoexcept
- Zc:implicitNoexcept
- -Zc:implicitNoexcept
ms.assetid: 71807652-6f9d-436b-899e-f52daa6f500b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e420017056d6857a2809ce6eb85fe99b6f3866f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379182"
---
# <a name="zcimplicitnoexcept-implicit-exception-specifiers"></a>/Zc:implicitNoexcept (specifikátory implicitních výjimek)

Když **/Zc: implicitnoexcept** je zadána možnost, kompilátor přidá implicitní [noexcept](../../cpp/noexcept-cpp.md) specifikátor výjimky kompilátoru definované speciální členské funkce a uživatelem definované destruktory a deallocators. Ve výchozím nastavení **/Zc: implicitnoexcept** je povoleno tak, aby odpovídala ISO C ++ 11 standardní. Vypnutí této možnosti vypnout zakáže implicitní `noexcept` na uživatelem definované destruktory a dealloacators a definované kompilátoru speciální členské funkce.

## <a name="syntax"></a>Syntaxe

> **/Zc:implicitNoexcept**[**-**]

## <a name="remarks"></a>Poznámky

**/ Zc: implicitnoexcept** říká kompilátoru podle části 15.4 ISO C ++ 11 standardní. Implicitně přidá `noexcept` výjimka specifikátor každý implicitně deklarovaný nebo explicitně uvedena speciální členské funkce – výchozí konstruktor, zkopírujte konstruktor, konstruktor move, destruktor, operátor přiřazení pro kopírování nebo přesunutí přiřazení operátor – a jednotlivé uživatelské destruktor nebo deallocator funkce. Uživatelem definované deallocator má implicitní `noexcept(true)` specifikátor výjimka. Uživatelem definované destruktory specifikátor implicitní výjimka je `noexcept(true)` Pokud třída obsažené členů nebo základní třída má destruktor, který není `noexcept(true)`. Pro generované kompilátorem speciální členské funkce, pokud žádné funkce přímo vyvolat tato funkce je efektivně `noexcept(false)`, specifikátor implicitní výjimka je `noexcept(false)`. Jinak specifikátor implicitní výjimka je `noexcept(true)`.

Kompilátor negeneruje specifikátor implicitní výjimky pro funkce deklarovat pomocí explicitní `noexcept` nebo `throw` specifikátory nebo `__declspec(nothrow)` atribut.

Ve výchozím nastavení **/Zc: implicitnoexcept** je povoleno. [/ Projektovou-](permissive-standards-conformance.md) možnost nemá vliv na **/Zc: implicitnoexcept**.

Pokud tato možnost je vypnuta zadáním **/Zc:implicitNoexcept-**, žádné specifikátory implicitních výjimek jsou generované kompilátorem. Toto chování je stejné jako Visual Studio 2013, pokud by mohla mít destruktory a deallocators, které neměl specifikátory výjimek `throw` příkazy. Ve výchozím nastavení a kdy **/Zc: implicitnoexcept** je zadán, pokud `throw` je příkaz zjistil v době běhu ve funkci s implicitní `noexcept(true)` specifikátor, dojde k vyvolání okamžitou `std::terminate`, a Normální unwinding chování pro obslužné rutiny výjimek není zaručena. Aby bylo možné identifikovat tuto situaci, kompilátor vygeneruje [upozornění kompilátoru (úroveň 1) C4297](../../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md). Pokud `throw` je záměrné, doporučujeme změnit své deklaraci funkce tak, aby měl explicitního `noexcept(false)` specifikátor místo použití **/Zc:implicitNoexcept-**.

Tento příklad ukazuje, jak – destruktor definovaný uživatelem, který má žádné explicitní výjimka specifikátor chová, kdy **/Zc: implicitnoexcept** je možnost nastavit nebo zakázána. Chcete-li zobrazit chování Pokud nastavíte, zkompilovat pomocí `cl /EHsc /W4 implicitNoexcept.cpp`. Zobrazit chování, pokud je zakázán, zkompilovat pomocí `cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp`.

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

Při kompilaci pomocí výchozí nastavení **/Zc: implicitnoexcept**, ukázky generuje tento výstup:

```Output
~B Exception caught
Unexpected throw caused std::terminate
Exit returning EXIT_FAILURE
```

Při kompilaci pomocí nastavení **/Zc:implicitNoexcept-**, ukázky generuje tento výstup:

```Output
~B Exception caught
~D Exception caught
Exit returning EXIT_SUCCESS
```

Další informace o problémech shoda v jazyce Visual C++, najdete v části [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Změnit **další možnosti** vlastnost, aby zahrnovala **/Zc: implicitnoexcept** nebo **/Zc:implicitNoexcept-** a potom zvolte **OK**.

## <a name="see-also"></a>Viz také

[/Zc (shoda)](../../build/reference/zc-conformance.md)<br/>
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[Specifikace výjimek (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[Ukončení](../../standard-library/exception-functions.md#terminate)<br/>
