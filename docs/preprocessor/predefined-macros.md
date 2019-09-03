---
title: Předdefinovaná makra
ms.custom: update_every_version
ms.date: 04/05/2019
f1_keywords:
- _ATL_VER
- __ATOM__
- __AVX__
- __AVX2__
- _CHAR_UNSIGNED
- __CLR_VER
- _CONTROL_FLOW_GUARD
- __COUNTER__
- __cplusplus
- __cplusplus_cli
- __cplusplus_winrt
- _CPPRTTI
- _CPPUNWIND
- __DATE__
- _DEBUG
- _DLL
- __FILE__
- __FUNCDNAME__
- __FUNCSIG__
- __FUNCTION__
- _INTEGRAL_MAX_BITS
- _ISO_VOLATILE
- _KERNEL_MODE
- __LINE__
- _M_AMD64
- _M_ARM
- _M_ARM_ARMV7VE
- _M_ARM_FP
- _M_ARM64
- _M_CEE
- _M_CEE_PURE
- _M_CEE_SAFE
- _M_FP_EXCEPT
- _M_FP_FAST
- _M_FP_PRECISE
- _M_FP_STRICT
- _M_IX86
- _M_IX86_FP
- _M_X64
- _MANAGED
- _MFC_VER
- _MSC_BUILD
- _MSC_EXTENSIONS
- _MSC_FULL_VER
- _MSC_VER
- _MSVC_LANG
- __MSVC_RUNTIME_CHECKS
- _MT
- _NATIVE_WCHAR_T_DEFINED
- _NO_SIZED_DEALLOCATION
- _OPENMP
- _PREFAST_
- _RESUMABLE_FUNCTIONS_SUPPORTED
- _RTC_CONVERSION_CHECKS_ENABLED
- __STDC__
- __STDC_HOSTED__
- __STDCPP_THREADS__
- __TIME__
- __TIMESTAMP__
- __VA_ARGS__
- _VC_NODEFAULTLIB
- _WCHAR_T_DEFINED
- _WIN32
- _WIN64
- _WINRT_DLL
- __func__
helpviewer_keywords:
- timestamps, preprocessor macro
- cl.exe compiler, version number
- version numbers, C/C++ compiler (cl.exe)
- macros, predefined C++
- preprocessor, macros
- predefined macros
- _ATL_VER macro
- __ATOM__ macro
- __AVX__ macro
- __AVX2__ macro
- _CHAR_UNSIGNED macro
- __CLR_VER macro
- _CONTROL_FLOW_GUARD macro
- __COUNTER__ macro
- __cplusplus macro
- __cplusplus_cli macro
- __cplusplus_winrt macro
- _CPPRTTI macro
- _CPPUNWIND macro
- __DATE__ macro
- _DEBUG macro
- _DLL macro
- __FILE__ macro
- __FUNCDNAME__ macro
- __FUNCSIG__ macro
- __FUNCTION__ macro
- _INTEGRAL_MAX_BITS macro
- _ISO_VOLATILE macro
- _KERNEL_MODE macro
- __LINE__ macro
- _M_AMD64 macro
- _M_ARM macro
- _M_ARM_ARMV7VE macro
- _M_ARM_FP macro
- _M_ARM64 macro
- _M_CEE macro
- _M_CEE_PURE macro
- _M_CEE_SAFE macro
- _M_FP_EXCEPT macro
- _M_FP_FAST macro
- _M_FP_PRECISE macro
- _M_FP_STRICT macro
- _M_IX86 macro
- _M_IX86_FP macro
- _M_X64 macro
- _MANAGED macro
- _MFC_VER macro
- _MSC_BUILD macro
- _MSC_EXTENSIONS macro
- _MSC_FULL_VER macro
- _MSC_VER macro
- _MSVC_LANG macro
- __MSVC_RUNTIME_CHECKS macro
- _MT macro
- _NATIVE_WCHAR_T_DEFINED macro
- _NO_SIZED_DEALLOCATION macro
- _OPENMP macro
- _PREFAST_ macro
- _RESUMABLE_FUNCTIONS_SUPPORTED macro
- _RTC_CONVERSION_CHECKS_ENABLED macro
- __STDC__ macro
- __STDC_HOSTED__ macro
- __STDCPP_THREADS__ macro
- __TIME__ macro
- __TIMESTAMP__ macro
- __VA_ARGS__ macro
- _VC_NODEFAULTLIB macro
- _WCHAR_T_DEFINED macro
- _WIN32 macro
- _WIN64 macro
- _WINRT_DLL macro
- __func__ identifier
ms.assetid: 1cc5f70a-a225-469c-aed0-fe766238e23f
ms.openlocfilehash: ab478cd8ac51b5cb88cec38f80541df8a7be2789
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222292"
---
# <a name="predefined-macros"></a>Předdefinovaná makra

Kompilátor jazyka Microsoft CC++ /COMPILER (MSVC) předdefinuje určitá makra preprocesoru v závislosti na jazyku (C nebo C++), cíli kompilace a zvolených možnostech kompilátoru.

MSVC podporuje Předdefinovaná makra preprocesoru, která vyžaduje standard ANSI/ISO C99, a normy ISO C++ 14 a C++ 17. Implementace také podporuje několik dalších maker preprocesoru specifických pro společnost Microsoft. Některá makra jsou definována pouze pro konkrétní prostředí sestavení nebo možnosti kompilátoru. S výjimkou případů, kdy je uvedeno jinak, jsou makra definována v rámci jednotky překladu, jako kdyby byla zadána jako **/d** argumenty možností kompilátoru. Při definování jsou makra rozšířena na zadané hodnoty preprocesorem před kompilací. Předdefinovaná makra nevyužívají žádné argumenty a nelze je předefinovat.

## <a name="standard-predefined-identifier"></a>Standardní předdefinovaný identifikátor

Kompilátor podporuje tento předdefinovaný identifikátor určený podle ISO C99 a ISO C++ 11.

- **&#95;&#95; funkce &#95;Func** Neúplný a Nekvalifikovaný název ohraničující funkce jako místní **statické** pole const typu Function.

    ```cpp
    void example(){
        printf("%s\n", __func__);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>Standardní Předdefinovaná makra

Kompilátor podporuje tato předdefinovaná makra určená standardy ISO C99 a ISO C++ 17.

- **&#95;cplusplus &#95;** Definováno jako hodnota celočíselného literálu, pokud je jednotka překladu kompilována jako C++. V opačném případě Nedefinováno.

- **&#95; Datum &#95; &#95;** Datum kompilace aktuálního zdrojového souboru. Datum je řetězcový literál konstantní délky ve tvaru *MMM DD RRRR*. Název měsíce *mmm* je stejný jako zkrácený název měsíce generovaný funkcí [asctime](../c-runtime-library/reference/asctime-wasctime.md) běhové knihovny jazyka C (CRT). Prvním znakem data *DD* je mezera, pokud je hodnota menší než 10. Toto makro je vždy definováno.

- **&#95; Soubor &#95; &#95;** Název aktuálního zdrojového souboru. Soubor se rozbalí do řetězcového literálu znaků. **&#95; &#95;&#95;** Chcete-li zajistit, aby se zobrazila úplná cesta k souboru, použijte [/FC (úplná cesta k souboru zdrojového kódu v diagnostice)](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md). Toto makro je vždy definováno.

- **&#95; Čára &#95; &#95;** Definováno jako celé číslo řádku v aktuálním zdrojovém souboru. Hodnota **&#95; &#95;řádku&#95; &#95;**  makra lze změnit pomocí `#line` směrnice. Toto makro je vždy definováno.

- **&#95; STDC &#95; &#95;** Definováno jako 1 pouze při kompilování jako C a pokud je určena možnost kompilátoru [/za](../build/reference/za-ze-disable-language-extensions.md) . V opačném případě Nedefinováno.

- **&#95;&#95;STDC&#95;&#95; Hosted** jako 1, pokud je implementace *hostovaná implementace*, jednu, která podporuje celou požadovanou standardní knihovnu. V opačném případě definováno jako 0.

- **&#95;&#95;STDCPP&#95;vlákna&#95;**  definovaná jako 1 pouze v případě, že program může mít více než jedno vlákno spuštění a kompilován jako C++. V opačném případě Nedefinováno.

- **&#95; Čas &#95; &#95;** Čas překladu předzpracované jednotky překladu. Čas je znakový literál řetězce ve tvaru *HH: mm: SS*, který je stejný jako čas VRÁCENÝ funkcí CRT [asctime](../c-runtime-library/reference/asctime-wasctime.md) . Toto makro je vždy definováno.

## <a name="microsoft-specific-predefined-macros"></a>Předdefinovaná makra specifická pro společnost Microsoft

MSVC podporuje tato další předdefinovaná makra.

- **&#95; Atom &#95; &#95;** Definováno jako 1, pokud je nastavena možnost kompilátoru [/favor: Atom](../build/reference/favor-optimize-for-architecture-specifics.md) a cíl kompilátoru je x86 nebo x64. V opačném případě Nedefinováno.

- **&#95; AVX &#95; &#95;** Definováno jako 1, pokud jsou nastaveny možnosti kompilátoru [/arch: AVX](../build/reference/arch-x86.md) nebo [/arch: AVX2](../build/reference/arch-x86.md) a cíl kompilátoru je x86 nebo x64. V opačném případě Nedefinováno.

- **&#95; AVX2 &#95; &#95;** Definováno jako 1, pokud je nastavena možnost kompilátoru [/arch: AVX2](../build/reference/arch-x86.md) a cíl kompilátoru je x86 nebo x64. V opačném případě Nedefinováno.

- **&#95;ZNAK&#95;bez znaménka** je definován jako 1, pokud je výchozí typ **znaku** bez znaménka. Tato hodnota je definována, pokud je nastaven parametr [/j (výchozí typ znaku není podepsaný)](../build/reference/j-default-char-type-is-unsigned.md) . V opačném případě Nedefinováno.

- **&#95;&#95;ver &#95;CLR** Definováno jako celočíselný literál, který představuje verzi modulu CLR (Common Language Runtime), která se používá ke kompilaci aplikace. Hodnota je kódována `Mmmbbbbb`ve formuláři, kde `M` je hlavní verzí modulu runtime, `mm` je podverze modulu runtime a `bbbbb` je číslo sestavení. **&#95;&#95;Verze&#95;CLR ver** je definována, pokud je nastavena možnost kompilátoru [/CLR](../build/reference/clr-common-language-runtime-compilation.md) . V opačném případě Nedefinováno.

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(__CLR_VER);
    }
    ```

- **&#95;Ochrana&#95;toku&#95;řízení** je definována jako 1, pokud je nastavena možnost kompilátoru [/Guard: CF (Povolit ochranu toku řízení)](../build/reference/guard-enable-control-flow-guard.md) . V opačném případě Nedefinováno.

- **&#95; Čítač &#95; &#95;** Rozšíří na celočíselný literál, který začíná na 0. Hodnota se zvýší o 1 pokaždé, když se použije ve zdrojovém souboru, nebo v zahrnutých hlavičkách zdrojového souboru. Čítač pamatuje svůj stav při použití předkompilovaných hlaviček. **&#95; &#95;&#95;** Toto makro je vždy definováno.

  Tento příklad používá `__COUNTER__` pro přiřazení jedinečných identifikátorů třem různým objektům stejného typu. `exampleClass` Konstruktor přebírá jako parametr celé číslo. V `main`aplikaci deklaruje aplikace tři objekty typu `exampleClass`pomocí `__COUNTER__` parametru jako parametr jedinečného identifikátoru:

    ```cpp
    // macro__COUNTER__.cpp
    // Demonstration of __COUNTER__, assigns unique identifiers to
    // different objects of the same type.
    // Compile by using: cl /EHsc /W4 macro__COUNTER__.cpp
    #include <stdio.h>

    class exampleClass {
        int m_nID;
    public:
        // initialize object with a read-only unique ID
        exampleClass(int nID) : m_nID(nID) {}
        int GetID(void) { return m_nID; }
    };

    int main()
    {
        // __COUNTER__ is initially defined as 0
        exampleClass e1(__COUNTER__);

        // On the second reference, __COUNTER__ is now defined as 1
        exampleClass e2(__COUNTER__);

        // __COUNTER__ is now defined as 2
        exampleClass e3(__COUNTER__);

        printf("e1 ID: %i\n", e1.GetID());
        printf("e2 ID: %i\n", e2.GetID());
        printf("e3 ID: %i\n", e3.GetID());

        // Output
        // ------------------------------
        // e1 ID: 0
        // e2 ID: 1
        // e3 ID: 2

        return 0;
    }
    ```

- **&#95;&#95;cplusplus&#95;CLI** definované jako celočíselná hodnota literálu 200406 při kompilování jako C++ a možnost kompilátoru [/CLR](../build/reference/clr-common-language-runtime-compilation.md) je nastavená. V opačném případě Nedefinováno. Při definování  **&#95; &#95;je cplusplus&#95;CLI** v platnosti v celé jednotce překladu.

    ```cpp
    // cplusplus_cli.cpp
    // compile by using /clr
    #include "stdio.h"
    int main() {
       #ifdef __cplusplus_cli
          printf("%d\n", __cplusplus_cli);
       #else
          printf("not defined\n");
       #endif
    }
    ```

- **&#95;&#95;cplusplus&#95;WinRT** byl definován jako celočíselná hodnota literálu 201009, C++ Pokud je kompilována jako a možnost kompilátoru [/ZW (prostředí Windows Runtime Compilation)](../build/reference/zw-windows-runtime-compilation.md) je nastavena. V opačném případě Nedefinováno.

- **&#95;CPPRTTI** Definováno jako 1, pokud je nastavena možnost kompilátoru [/gr (povolit informace běhového typu)](../build/reference/gr-enable-run-time-type-information.md) . V opačném případě Nedefinováno.

- **&#95;CPPUNWIND** Definováno jako 1, pokud je jeden nebo více [/GX (povolení zpracování výjimek)](../build/reference/gx-enable-exception-handling.md), [/CLR (kompilace modulu](../build/reference/clr-common-language-runtime-compilation.md)CLR) nebo [/EH (model zpracování výjimek)](../build/reference/eh-exception-handling-model.md) nastaveny možnosti kompilátoru. V opačném případě Nedefinováno.

- **&#95;Ladit** Definováno jako 1, pokud je nastavena možnost kompilátoru [/LDD](../build/reference/md-mt-ld-use-run-time-library.md), [/MDD](../build/reference/md-mt-ld-use-run-time-library.md)nebo [/MTD](../build/reference/md-mt-ld-use-run-time-library.md) . V opačném případě Nedefinováno.

- DLL definovaná jako 1, pokud je nastavena možnost kompilátoru [/MD](../build/reference/md-mt-ld-use-run-time-library.md) nebo [/MDD](../build/reference/md-mt-ld-use-run-time-library.md) (Vícevláknová knihovna DLL).  **&#95;** V opačném případě Nedefinováno.

- **&#95; FUNCDNAME &#95; &#95;** Definováno jako řetězcový literál, který obsahuje [dekorované názvy](../build/reference/decorated-names.md) ohraničující funkce. Makro je definováno pouze v rámci funkce. Pokud použijete možnost kompilátoru [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) nebo [/p](../build/reference/p-preprocess-to-a-file.md) , není  **&#95;FUNCDNAME&#95; makro rozbalené. &#95;**

   Tento příklad používá `__FUNCDNAME__`makra, `__FUNCSIG__`a `__FUNCTION__` k zobrazení informací o funkci.

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- **&#95; FUNCSIG &#95; &#95;** Definováno jako řetězcový literál, který obsahuje signaturu uzavírací funkce. Makro je definováno pouze v rámci funkce. Pokud použijete možnost kompilátoru [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) nebo [/p](../build/reference/p-preprocess-to-a-file.md) , není  **&#95;FUNCSIG&#95; makro rozbalené. &#95;** Při kompilaci pro 64 cíl je `__cdecl` konvence volání standardně. Příklad použití naleznete `__FUNCDNAME__` v makru.

- **&#95; Funkce &#95; &#95;** Definováno jako řetězcový literál, který obsahuje nedekorovaný název ohraničující funkce. Makro je definováno pouze v rámci funkce. [](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)  **&#95;Makro funkce&#95; není rozbaleno, pokud použijete možnost kompilátoru/EP nebo &#95;** [/p](../build/reference/p-preprocess-to-a-file.md) . Příklad použití naleznete `__FUNCDNAME__` v makru.

- **maximální počet&#95;bitů v integrálu&#95; &#95;** Definováno jako celočíselná hodnota literálu 64, maximální velikost (v bitech) pro celočíselný typ, který není vektor. Toto makro je vždy definováno.

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", _INTEGRAL_MAX_BITS);
   }
   ```

- **&#95; INTELLISENSE &#95; &#95;** Definováno jako 1 během průchodu kompilátoru IntelliSense v integrovaném vývojovém prostředí sady Visual Studio. V opačném případě Nedefinováno. Toto makro lze použít k ochraně kódu, který kompilátor IntelliSense nepochopení nebo používá pro přepínání mezi kompilátorem sestavení a IntelliSense. Další informace najdete v tématu [Poradce při potížích s pomalými typy funkcí IntelliSense](https://devblogs.microsoft.com/cppblog/troubleshooting-tips-for-intellisense-slowness/).

- **&#95;ISO&#95;volatile** definovaná jako 1, pokud je nastavená možnost kompilátoru [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) . V opačném případě Nedefinováno.

- **&#95;Režim&#95;jádra** definovaný jako 1, pokud je nastavena možnost kompilátoru [/kernel (vytvoření binárního režimu jádra)](../build/reference/kernel-create-kernel-mode-binary.md) . V opačném případě Nedefinováno.

- **&#95;M&#95;amd64** Definováno jako celočíselná hodnota literálu 100 pro kompilace, které cílí na procesory x64. V opačném případě Nedefinováno.

- **&#95;M&#95;ARM** Definováno jako celočíselná hodnota literálu 7 pro kompilace, které cílí na procesory ARM. V opačném případě Nedefinováno.

- **&#95;M&#95;ARM&#95;ARMV7VE** definováno jako 1, pokud je možnost kompilátoru [/arch: ARMV7VE](../build/reference/arch-arm.md) nastavená pro kompilace, které cílí na procesory ARM. V opačném případě Nedefinováno.

- **&#95;M&#95;ARM&#95;FP** definované jako celočíselná hodnota literálu, která označuje, která možnost kompilátoru [/arch](../build/reference/arch-arm.md) byla nastavena pro cíle procesoru ARM. V opačném případě Nedefinováno.

  - Hodnota v rozsahu 30-39, pokud nebyla zadána `/arch` žádná možnost ARM, což značí, že byla nastavena výchozí architektura pro ARM`VFPv3`().

  - Hodnota v rozsahu 40-49, pokud `/arch:VFPv4` byla nastavena.

  - Další informace najdete v tématu [/arch (ARM)](../build/reference/arch-arm.md).

- **&#95;ARM64&#95;M** Definováno jako 1 pro kompilace, které cílí na 64 procesorů ARM. V opačném případě Nedefinováno.

- **&#95;M&#95;CEE** definováno jako 001, pokud je nastavena možnost kompilátoru [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md) . V opačném případě Nedefinováno.

- **M&#95;CEE&#95;Pure &#95;** Zastaralé od začátku v aplikaci Visual Studio 2015. Definováno jako 001, pokud je nastavena možnost [/clr: Pure](../build/reference/clr-common-language-runtime-compilation.md) . V opačném případě Nedefinováno.

- **M&#95;CEE&#95;Safe &#95;** Zastaralé od začátku v aplikaci Visual Studio 2015. Definováno jako 001, pokud je nastavena možnost [/clr: Safe](../build/reference/clr-common-language-runtime-compilation.md) kompilátoru. V opačném případě Nedefinováno.

- **&#95;M&#95;FP&#95;s výjimkou** definování jako 1, je-li nastavena možnost kompilátoru [/FP: except](../build/reference/fp-specify-floating-point-behavior.md) nebo [/FP: Strict](../build/reference/fp-specify-floating-point-behavior.md) . V opačném případě Nedefinováno.

- **&#95;M&#95;FP&#95;Fast** definováno jako 1, pokud je nastavena možnost kompilátoru [/FP: Fast](../build/reference/fp-specify-floating-point-behavior.md) . V opačném případě Nedefinováno.

- **&#95;M&#95;FP&#95;přesně** definované jako 1, pokud je nastavena možnost [/FP: přesný](../build/reference/fp-specify-floating-point-behavior.md) kompilátor. V opačném případě Nedefinováno.

- **&#95;M&#95;FP&#95;Strict** definováno jako 1, pokud je nastavena možnost kompilátoru [/FP: Strict](../build/reference/fp-specify-floating-point-behavior.md) . V opačném případě Nedefinováno.

- **&#95;IX86&#95;M** Definováno jako celočíselná hodnota literálu 600 pro kompilace, které cílí na procesory x86. Toto makro není definované pro cíle kompilace x64 nebo ARM.

- **&#95;M&#95;IX86&#95;FP** definované jako celočíselná hodnota literálu, která označuje možnost kompilátoru [/arch](../build/reference/arch-arm.md) , která byla nastavena, nebo výchozí. Toto makro je vždy definováno, je-li cílem kompilace procesor x86. V opačném případě Nedefinováno. Při definování je tato hodnota:

  - 0, `/arch:IA32` Pokud byla nastavena možnost kompilátoru.

  - 1, `/arch:SSE` Pokud byla nastavena možnost kompilátoru.

  - 2 `/arch:SSE2`, pokud byla `/arch:AVX`nastavena možnost `/arch:AVX2` kompilátoru, nebo. Tato hodnota je výchozí, pokud `/arch` nebyla zadána možnost kompilátoru. Je `/arch:AVX` -li parametr zadán, je také definováno makro **&#95; &#95;AVX&#95;** . Je `/arch:AVX2` -li parametr zadán, jsou rovněž definovány současně **&#95; &#95;AVX&#95;** i **&#95; &#95;AVX2&#95;** .

  - Další informace najdete v tématu [/arch (x86)](../build/reference/arch-x86.md).

- **&#95;M&#95;x64** Definováno jako celočíselná hodnota literálu 100 pro kompilace, které cílí na procesory x64. V opačném případě Nedefinováno.

- **&#95;Spravované** Definováno jako 1, pokud je nastavena možnost kompilátoru [/CLR](../build/reference/clr-common-language-runtime-compilation.md) . V opačném případě Nedefinováno.

- **&#95;sestavení&#95;MSC** Definováno jako celočíselný literál, který obsahuje element číslo revize čísla verze kompilátoru. Číslo revize je čtvrtý prvek čísla verze s hodnotami oddělenými tečkami. Například pokud je číslo verze společnosti Microsoft C/C++ Compiler 15.00.20706.01, makro  **&#95;sestavení MSC&#95;** je vyhodnoceno jako 1. Toto makro je vždy definováno.

- **&#95;Přípona MSC&#95;** definovaná jako 1, pokud je nastavena možnost kompilátoru on- [/ze (Povolit jazykové rozšíření)](../build/reference/za-ze-disable-language-extensions.md) . V opačném případě Nedefinováno.

- MSC – úplný ver **&#95; &#95;&#95;** Definováno jako celočíselný literál, který kóduje prvky hlavního, vedlejšího a čísla sestavení čísla verze kompilátoru. Hlavní číslo je první prvek čísla verze s hodnotami oddělenými tečkami, vedlejší číslo je druhý prvek a číslo sestavení je třetí prvek. Například pokud je číslo verze MicrosoftC++ C/Compiler 15.00.20706.01, makro  **&#95;MSC&#95;Full&#95;ver** se vyhodnotí jako 150020706. Chcete `cl /?` -li zobrazit číslo verze kompilátoru, zadejte na příkazovém řádku. Toto makro je vždy definováno.

- **&#95;MSC&#95;– ver** Definováno jako celočíselný literál, který kóduje hlavní a vedlejší číslo prvků čísla verze kompilátoru. Hlavní číslo je první prvek čísla verze s hodnotami oddělenými tečkami a vedlejší číslo je druhým prvkem. Například pokud je číslo verze Microsoft C/C++ Compiler 17.00.51106.1, makro  **&#95;MSC&#95;ver** se vyhodnotí jako 1700. Chcete `cl /?` -li zobrazit číslo verze kompilátoru, zadejte na příkazovém řádku. Toto makro je vždy definováno.

   |Verze sady Visual Studio|**&#95;MSC&#95;– VER**|
   |-|-|
   |Visual Studio 6.0|1200|
   |Visual Studio .NET 2002 (7,0)|1300|
   |Visual Studio .NET 2003 (7,1)|1310|
   |Visual Studio 2005 (8,0)|1400|
   |Visual Studio 2008 (9,0)|1500|
   |Visual Studio 2010 (10,0)|1600|
   |Visual Studio 2012 (11,0)|1700|
   |Visual Studio 2013 (12,0)|1800|
   |Visual Studio 2015 (14,0)|1900|
   |Visual Studio 2017 RTW (15,0)|1910|
   |Visual Studio 2017 verze 15,3|1911|
   |Visual Studio 2017 verze 15.5|1912|
   |Visual Studio 2017 verze 15.6|1913|
   |Visual Studio 2017 verze 15,7|1914|
   |Visual Studio 2017 verze 15.8|1915|
   |Visual Studio 2017 verze 15,9|1916|
   |Visual Studio 2019 RTW (16,0)|1920|
   |Visual Studio 2019 verze 16,1|1921|
   |Visual Studio 2019 verze 16,2|1922|
   |Visual Studio 2019 verze 16,3|1923|

   Chcete-li otestovat verze kompilátoru nebo aktualizace v dané verzi sady Visual Studio nebo po, použijte **>=** operátor. Můžete ji použít v podmíněných direktivách k  **&#95;porovnání&#95;MSC ver** s touto známou verzí. Pokud máte několik vzájemně se vylučujících verzí, které je třeba porovnat, porovnejte je podle čísla verze v sestupném pořadí. Například tento kód kontroluje kompilátory vydané v aplikaci Visual Studio 2017 nebo novější. Dále kontroluje kompilátory vydané v nebo po aplikaci Visual Studio 2015. Pak zkontroluje všechny kompilátory vydané před Visual Studio 2015:

   ```cpp
   #if _MSC_VER >= 1910
   // . . .
   #elif _MSC_VER >= 1900
   // . . .
   #else
   // . . .
   #endif
   ```

   Další informace naleznete v tématu [Visual C++ Compiler verze](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/) na blogu týmu C++ společnosti Microsoft.

- **&#95;MSVC&#95;lang** definovaný jako celočíselný literál, který určuje C++ jazykový Standard cílený kompilátorem. Je nastaven pouze v kódu kompilovaném jako C++. Makro je hodnota celočíselného literálu 201402L ve výchozím nastavení nebo při určení možnosti kompilátoru [/std: c++ 14](../build/reference/std-specify-language-standard-version.md) . Makro je nastaveno na 201703L, pokud je zadána možnost kompilátoru [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) . Je nastavena na vyšší, nespecifikovanou hodnotu, pokud je zadána možnost [/std: c + + nejnovější](../build/reference/std-specify-language-standard-version.md) . V opačném případě není makro definováno. **&#95;MSVC&#95;LANG** – makro a [/STD (určení standardní jazykové verze)](../build/reference/std-specify-language-standard-version.md) jsou k dispozici od verze Visual Studio 2015 Update 3 – možnosti kompilátoru.

- **&#95;&#95;Pokud&#95;je&#95;** nastavena jedna z možností kompilátoru [/RTC](../build/reference/rtc-run-time-error-checks.md) , kontroly modulu runtime MSVC definovány jako 1. V opačném případě Nedefinováno.

- **&#95;MT** Definováno jako 1, pokud je zadána [/MD nebo/MDD](../build/reference/md-mt-ld-use-run-time-library.md) (VÍCEVLÁKNOVÁ knihovna DLL) nebo [/Mt nebo/MTD](../build/reference/md-mt-ld-use-run-time-library.md) (vícevláknové). V opačném případě Nedefinováno.

- **&#95;NATIVNÍ&#95;WCHAR&#95;T&#95;definovaná** jako 1, když je nastavená možnost kompilátoru [/Zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) . V opačném případě Nedefinováno.

- **&#95;OPENMP – direktiva** Definováno jako celočíselný literál 200203, pokud je nastavena možnost kompilátoru [/OpenMP (povolit podporu openmp 2,0)](../build/reference/openmp-enable-openmp-2-0-support.md) . Tato hodnota představuje datum specifikace OpenMP implementovaného MSVC. V opačném případě Nedefinováno.

   ```cpp
   // _OPENMP_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", _OPENMP);
   }
   ```

- **&#95;Před&#95; rychlým** Definováno jako 1, pokud je nastavena možnost kompilátoru [/analyze](../build/reference/analyze-code-analysis.md) . V opačném případě Nedefinováno.

- **&#95;&#95; Časové &#95;razítko** Definováno jako řetězcový literál, který obsahuje datum a čas poslední změny aktuálního zdrojového souboru, ve zkráceném formátu s konstantní délkou vrácenou funkcí CRT [asctime](../c-runtime-library/reference/asctime-wasctime.md) , `Fri 19 Aug 13:32:58 2016`například. Toto makro je vždy definováno.

- **&#95;VC&#95;NODEFAULTLIB** definováno jako 1, pokud je nastavena možnost kompilátoru [/zl (vynechání názvu výchozí knihovny)](../build/reference/zl-omit-default-library-name.md) . V opačném případě Nedefinováno.

- **&#95;WCHAR&#95;T&#95;definována** definovaná jako 1, pokud je nastavena výchozí hodnota kompilátoru [/Zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) . **&#95;WCHAR&#95;T&#95;definované** – makro je definováno, ale nemá žádnou hodnotu, pokud `/Zc:wchar_t-` – možnost kompilátoru je nastavena, a **wchar_t** je definována v hlavičkovém souboru součástí vaší projekt. V opačném případě Nedefinováno.

- **&#95;Win32** Definováno jako 1, pokud je cíl kompilace 32-bit ARM, 64 bitů ARM, x86 nebo x64. V opačném případě Nedefinováno.

- **&#95;Prostředí Win64** Definováno jako 1, pokud je cíl kompilace 64-bit ARM nebo x64. V opačném případě Nedefinováno.

- **&#95;Knihovna&#95;WINRT DLL** , která je definována jako C++ 1, je-li zkompilována jako a jsou nastaveny možnosti kompilátoru [/ZW (prostředí Windows Runtime Compilation)](../build/reference/zw-windows-runtime-compilation.md) a [/ld nebo/LDD](../build/reference/md-mt-ld-use-run-time-library.md) . V opačném případě Nedefinováno.

Žádná makra preprocesoru, která neidentifikují verzi knihovny ATL nebo MFC, jsou předdefinovány kompilátorem. Hlavičky knihoven ATL a MFC definují tato makra verze interně. Nejsou definovány v direktivách preprocesoru, které byly provedeny před tím, než je obsažena požadovaná hlavička.

- **&#95;Verze&#95;ATL ver** definovaná \<v atldef. h > jako celočíselný literál, který kóduje číslo verze ATL.

- **&#95;Verze&#95;MFC ver** definovaná \<v afxver_. h > jako celočíselný literál, který kóduje číslo verze knihovny MFC.

## <a name="see-also"></a>Viz také:

[Makra (C/C++)](../preprocessor/macros-c-cpp.md)<br/>
[Operátory preprocesoru](../preprocessor/preprocessor-operators.md)<br/>
[Direktivy preprocesoru](../preprocessor/preprocessor-directives.md)