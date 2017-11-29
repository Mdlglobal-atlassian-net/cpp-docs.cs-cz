---
title: "-Zc: implicitNoexcept (specifikátory implicitních výjimek) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /Zc:implicitNoexcept
dev_langs: C++
helpviewer_keywords:
- /Zc:implicitNoexcept
- Zc:implicitNoexcept
- -Zc:implicitNoexcept
ms.assetid: 71807652-6f9d-436b-899e-f52daa6f500b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 20789d226ace8ba41a9635f0039274b68d37922c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="zcimplicitnoexcept-implicit-exception-specifiers"></a>/Zc:implicitNoexcept (specifikátory implicitních výjimek)
Když **/Zc: implicitnoexcept** je zadána možnost, kompilátor přidá implicitní [noexcept](../../cpp/noexcept-cpp.md) specifikátor výjimky kompilátoru definované speciální členské funkce a uživatelem definované destruktory a deallocators. Ve výchozím nastavení **/Zc: implicitnoexcept** je povoleno tak, aby odpovídala ISO C ++ 11 standardní. Vypnutí této možnosti vypnout zakáže implicitní `noexcept` na uživatelem definované destruktory a dealloacators a definované kompilátoru speciální členské funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
/Zc:implicitNoexcept[-]  
```  
  
#### <a name="parameters"></a>Parametry  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení a pokud **/Zc: implicitnoexcept** je zadán, kompilátor postupuje podle části 15.4 ISO C ++ 11 standardní a implicitně přidá `noexcept` specifikátor výjimky pro každé implicitně deklarovaný nebo explicitně uvedena speciální členské funkce – výchozí konstruktor, kopírovacího konstruktoru, konstruktor move, – destruktor, operátor přiřazení kopírování nebo přesunutí operátor přiřazení – a jednotlivé uživatelské destruktor nebo deallocator funkce. Uživatelem definované deallocator má implicitní `noexcept(true)` specifikátor výjimka. Uživatelem definované destruktory specifikátor implicitní výjimka je `noexcept(true)` Pokud třída obsažené členů nebo základní třída má destruktor, který není `noexcept(true)`. Pro generované kompilátorem speciální členské funkce, pokud žádné funkce přímo vyvolat tato funkce je efektivně `noexcept(false)`, specifikátor implicitní výjimka je `noexcept(false)`. Jinak specifikátor implicitní výjimka je `noexcept(true)`.  
  
 Kompilátor negeneruje specifikátor implicitní výjimky pro funkce deklarovat pomocí explicitní `noexcept` nebo `throw` specifikátory nebo `__declspec(nothrow)` atribut.  
  
 Pokud tato možnost je vypnuta zadáním **/Zc:implicitNoexcept-**, žádné specifikátory implicitních výjimek jsou generované kompilátorem. Toto chování je stejné jako Visual Studio 2013, pokud by mohla mít destruktory a deallocators, které neměl specifikátory výjimek `throw` příkazy. Ve výchozím nastavení a kdy **/Zc: implicitnoexcept** je zadán, pokud `throw` je příkaz zjistil v době běhu ve funkci s implicitní `noexcept(true)` specifikátor, dojde k vyvolání okamžitou `std::terminate`, a Normální unwinding chování pro obslužné rutiny výjimek není zaručena. Aby bylo možné identifikovat tuto situaci, kompilátor vygeneruje [upozornění kompilátoru (úroveň 1) C4297](../../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md). Pokud `throw` je záměrné, doporučujeme změnit své deklaraci funkce tak, aby měl explicitního `noexcept(false)` specifikátor místo použití **/Zc:implicitNoexcept-**.  
  
 Tento příklad ukazuje, jak – destruktor definovaný uživatelem, který má žádné explicitní výjimka specifikátor chová, kdy **/Zc: implicitnoexcept** je možnost nastavit nebo zakázána. Chcete-li zobrazit chování Pokud nastavíte, zkompilovat pomocí `cl /EHsc /W4 implicitNoexcept.cpp`. Zobrazit chování, pokud je zakázán, zkompilovat pomocí `cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp`.  
  
```  
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
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **C/C++** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  Změnit **další možnosti** vlastnost, aby zahrnovala **/Zc: implicitnoexcept** nebo **/Zc:implicitNoexcept-** a potom zvolte **OK**.  
  
## <a name="see-also"></a>Viz také  
 [/Zc (shoda)](../../build/reference/zc-conformance.md)   
 [noexcept](../../cpp/noexcept-cpp.md)   
 [Specifikace výjimek (throw)](../../cpp/exception-specifications-throw-cpp.md)   
 [ukončení](../../standard-library/exception-functions.md#terminate)