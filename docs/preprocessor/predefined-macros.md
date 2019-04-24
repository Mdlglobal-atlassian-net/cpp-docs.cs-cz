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
ms.openlocfilehash: dedcab9b0addd3696749b50fef92b70081981c03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179903"
---
# <a name="predefined-macros"></a>Předdefinovaná makra

Kompilátor Microsoft C/C++ (MSVC) predefines určité makra preprocesoru, v závislosti na jazyk (C nebo C++), cíl kompilace a možnosti zvolené kompilátoru.

MSVC podporuje předdefinovaná makra preprocesoru vyžadované standardu ANSI/ISO C99 a ISO C ++ 14 a standardů C ++ 17. Implementace podporuje také několik Další makra preprocesoru specifické pro společnost Microsoft. Některé makra jsou definována pouze pro prostředí konkrétní sestavení nebo možnosti kompilátoru. S výjimkou toho, pokud jste si poznamenali, makra jsou definována v jednotce překladu, jako kdyby byly zadány jako **/D** argumenty – možnost kompilátoru. Když je definován, jsou makra analyzována pomocí preprocesoru před kompilací do zadaných hodnot. Předdefinovaná makra nepřebírají žádné argumenty a nejde předefinovat.

## <a name="standard-predefined-identifier"></a>Standardní předdefinovaný identifikátor

Kompilátor podporuje tento předdefinovaný identifikátor určené ISO C99 a ISO C ++ 11.

- **&#95;&#95;Func&#95; &#95;**  nekvalifikovaný, prostý název nadřazené funkce jako místní funkce **konstrukce static const** pole **char**.

    ```cpp
    void example(){
        printf("%s\n", __func__);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>Standardní předdefinovaná makra

Kompilátor podporuje těchto předdefinovaných makrech určené ISO C ++ 17 standardy a ISO C99.

- **&#95;&#95;cplusplus** definován jako celočíselnou hodnotu literálu při kompilaci jednotky překladu jako C++. V opačném případě undefined.

- **&#95;&#95;DATUM&#95; &#95;**  datum kompilace aktuálního zdrojového souboru. Datum je řetězec o délce konstantní literál ve formátu *Mmm dd, rrrr*. Název měsíce *Mmm* je stejné jako zkrácený název měsíce vygenerované pomocí knihovny C Runtime (CRT) [asctime –](../c-runtime-library/reference/asctime-wasctime.md) funkce. První znak datum *dd* je místo, pokud je hodnota menší než 10. Toto makro je vždy definováno.

- **&#95;&#95;SOUBOR&#95; &#95;**  název aktuálního zdrojového souboru. **&#95;&#95;SOUBOR&#95; &#95;**  rozbalí na řetězcový literál znaku. Chcete-li zajistit, že se zobrazí úplnou cestu k souboru, použijte [/FC (úplná cesta ze souboru zdrojového kódu v diagnostice)](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md). Toto makro je vždy definováno.

- **&#95;&#95;ŘÁDEK&#95; &#95;**  definován jako celé číslo řádku v aktuálním zdrojovém souboru. Hodnota **&#95; &#95;řádku&#95; &#95;** makra lze změnit pomocí `#line` směrnice. Toto makro je vždy definováno.

- **&#95;&#95;STDC&#95; &#95;**  definována jako 1, jenom když se kompilují jako C a pokud [/Za](../build/reference/za-ze-disable-language-extensions.md) je zadána možnost kompilátoru. V opačném případě undefined.

- **&#95;&#95;STDC&#95;HOSTOVANÁ&#95; &#95;**  definována jako 1, pokud je implementace *hostované implementace*, ten, který podporuje celou vyžaduje standardní knihovnu. V opačném případě definováno jako 0.

- **&#95;&#95;STDCPP&#95;vlákna&#95; &#95;**  definováno jako 1 pouze v případě program může mít více než jedno vlákno provádění a zkompilovat jako C++. V opačném případě undefined.

- **&#95;&#95;ČAS&#95; &#95;**  doby překladu jednotky předzpracovaná překladu. Čas je řetězec znaků literálu ve formátu *hh: mm:*, stejné jako čas vrácený CRT [asctime –](../c-runtime-library/reference/asctime-wasctime.md) funkce. Toto makro je vždy definováno.

## <a name="microsoft-specific-predefined-macros"></a>Předdefinovaná makra specifická pro společnost Microsoft

MSVC podporuje tyto dodatečné předdefinovaná makra.

- **&#95;&#95;ATOM&#95; &#95;**  definována jako 1, pokud [/favor:ATOM](../build/reference/favor-optimize-for-architecture-specifics.md) – možnost kompilátoru je nastavená a je cílem kompilátoru je x86 nebo x64. V opačném případě undefined.

- **&#95;&#95;AVX&#95; &#95;**  definována jako 1, pokud [/arch: AVX](../build/reference/arch-x86.md) nebo [/arch: avx2](../build/reference/arch-x86.md) jsou nastavené možnosti kompilátoru a je cílem kompilátoru x86 nebo x64. V opačném případě undefined.

- **&#95;&#95;AVX2&#95; &#95;**  definována jako 1, pokud [/arch: avx2](../build/reference/arch-x86.md) – možnost kompilátoru je nastavená a je cílem kompilátoru je x86 nebo x64. V opačném případě undefined.

- **&#95;CHAR&#95;UNSIGNED char** definována jako 1, pokud výchozí **char** typ není podepsaný. Tato hodnota je definována při [/J (výchozí znakový typ není podepsán)](../build/reference/j-default-char-type-is-unsigned.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;&#95;CLR&#95;VER** definované jako celočíselný literál, který představuje verze Common Language Runtime (CLR) použít ke kompilaci aplikace. Hodnota je kódovány ve formě `Mmmbbbbb`, kde `M` je hlavní verzí modulu runtime, `mm` je dílčí verzí modulu runtime a `bbbbb` je číslo sestavení. **&#95;&#95;CLR&#95;VER** je definováno, pokud [/CLR](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(__CLR_VER);
    }
    ```

- **&#95;Ovládací PRVEK&#95;TOK&#95;GUARD** definována jako 1, pokud [/Guard: CF (povolení ochrany toku řízení)](../build/reference/guard-enable-control-flow-guard.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;&#95;Čítač&#95; &#95;**  Expands na celé literál, který začíná hodnotou 0. Hodnota se zvyšuje o 1 pokaždé, když se používá ve zdrojovém souboru nebo v záhlaví zahrnutém ve zdrojového souboru. **&#95;&#95;Čítač&#95; &#95;**  si pamatuje svůj stav při použití předkompilovaných hlaviček. Toto makro je vždy definováno.

  Tento příklad používá `__COUNTER__` pro přiřazení jedinečných identifikátorů pro tři různé objekty stejného typu. `exampleClass` Konstruktoru přijímá jako parametr celé číslo. V `main`, aplikace deklaruje především tři objekty typu `exampleClass`pomocí `__COUNTER__` jako parametrem jedinečného identifikátoru:

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

- **&#95;&#95;cplusplus&#95;rozhraní příkazového řádku** definované jako literál celočíselná hodnota 200406 při kompilaci jako C++ a [/CLR](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru je nastavena. V opačném případě undefined. Při definování,  **&#95; &#95;cplusplus&#95;rozhraní příkazového řádku** je v platnosti jednotky překladu.

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

- **&#95;&#95;cplusplus&#95;winrt** definován jako literál celočíselnou hodnotu 201009 při kompilaci jako C++ a [/ZW (kompilace Windows Runtime)](../build/reference/zw-windows-runtime-compilation.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;CPPRTTI** definována jako 1, pokud [/GR (povolení běhové informace o typu)](../build/reference/gr-enable-run-time-type-information.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;CPPUNWIND** definována jako 1, pokud jeden nebo více následujících [/GX (povolení zpracování výjimek)](../build/reference/gx-enable-exception-handling.md), [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md), nebo [/EH (výjimka zpracování modelu)](../build/reference/eh-exception-handling-model.md) jsou nastavené možnosti kompilátoru. V opačném případě undefined.

- **&#95;LADĚNÍ** definována jako 1, pokud [/LDd](../build/reference/md-mt-ld-use-run-time-library.md), [/MDd](../build/reference/md-mt-ld-use-run-time-library.md), nebo [/MTD](../build/reference/md-mt-ld-use-run-time-library.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;Knihovny DLL** definována jako 1, pokud [/MD](../build/reference/md-mt-ld-use-run-time-library.md) nebo [/MDd](../build/reference/md-mt-ld-use-run-time-library.md) – možnost kompilátoru (vícevláknové DLL) je nastavena. V opačném případě undefined.

- **&#95;&#95;FUNCDNAME&#95; &#95;**  definovaný jako řetězec literálu, který obsahuje [dekorovaného názvu](../build/reference/decorated-names.md) nadřazené funkce. Makro je definováno pouze v rámci funkce. **&#95; &#95;FUNCDNAME&#95; &#95;** – makro není rozbalený, použijete [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) nebo [/P](../build/reference/p-preprocess-to-a-file.md) – možnost kompilátoru.

   V tomto příkladu `__FUNCDNAME__`, `__FUNCSIG__`, a `__FUNCTION__` makra k zobrazení informací o funkci.

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- **&#95;&#95;FUNCSIG&#95; &#95;**  definovaný jako řetězec literálu, který obsahuje podpis nadřazené funkce. Makro je definováno pouze v rámci funkce. **&#95; &#95;FUNCSIG&#95; &#95;** – makro není rozbalený, použijete [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) nebo [/P](../build/reference/p-preprocess-to-a-file.md) – možnost kompilátoru. Při kompilaci pro 64bitové cílové je konvence volání `__cdecl` ve výchozím nastavení. Příklad použití, najdete v článku `__FUNCDNAME__` – makro.

- **&#95;&#95;FUNKCE&#95; &#95;**  definovaný jako řetězec literálu, který obsahuje nedekorovaný název nadřazené funkce. Makro je definováno pouze v rámci funkce. **&#95; &#95;Funkce&#95; &#95;** – makro není rozbalený, použijete [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) nebo [/P](../build/reference/p-preprocess-to-a-file.md) – možnost kompilátoru. Příklad použití, najdete v článku `__FUNCDNAME__` – makro.

- **&#95;INTEGRÁLNÍ&#95;maximální&#95;BITS** definované jako literál celočíselnou hodnotu 64, maximální velikost (v bitech) integrálního typu bez vektoru. Toto makro je vždy definováno.

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", _INTEGRAL_MAX_BITS);
   }
   ```

- **&#95;&#95;Technologie INTELLISENSE&#95; &#95;**  definovaný jako předat 1 během kompilátoru technologie IntelliSense v integrovaném vývojovém prostředí sady Visual Studio. V opačném případě undefined. Toto makro můžete použít pro ochranu kódu kompilátoru IntelliSense nebude pochopit, nebo pomocí něho můžete přepínat mezi sestavení a technologie IntelliSense kompilátoru. Další informace najdete v tématu [řešení potíží s tipy pro IntelliSense pomalost](https://devblogs.microsoft.com/cppblog/troubleshooting-tips-for-intellisense-slowness/).

- **&#95;ISO&#95;VOLATILE** definována jako 1, pokud [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;JÁDRA&#95;režimu** definována jako 1, pokud [/Kernel (vytvoření binárního režimu jádra)](../build/reference/kernel-create-kernel-mode-binary.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;M&#95;AMD64** definovaný jako celočíselný literál hodnotu 100 kompilací této cílové x64 procesory. V opačném případě undefined.

- **&#95;M&#95;ARM** definován jako literál celočíselnou hodnotu 7 pro soubory, které se zaměřují procesory ARM. V opačném případě undefined.

- **&#95;M&#95;ARM&#95;ARMV7VE** definována jako 1, pokud [/arch:ARMv7VE](../build/reference/arch-arm.md) – možnost kompilátoru je nastaven pro kompilaci, které se zaměřují procesory ARM. V opačném případě undefined.

- **&#95;M&#95;ARM&#95;FP** definován jako literál celočíselnou hodnotu, která označuje, které [/arch](../build/reference/arch-arm.md) byl nastaven – možnost kompilátoru pro cíle procesoru ARM. V opačném případě undefined.

  - Číslo v rozsahu 30-39, pokud žádné `/arch` byla zadána možnost ARM, určující výchozí architektura pro ARM byl nastaven (`VFPv3`).

  - Hodnota v rozsahu 40-49 if `/arch:VFPv4` byl nastaven.

  - Další informace najdete v tématu [/arch (ARM)](../build/reference/arch-arm.md).

- **&#95;M&#95;ARM64** definována jako 1 pro soubory, které se zaměřují na 64bitové procesory ARM. V opačném případě undefined.

- **&#95;M&#95;CEE** definované jako 001 Pokud některý [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;M&#95;CEE&#95;prázdná** zastaralé od verze Visual Studio 2015. Definován jako 001 if [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;M&#95;CEE&#95;BEZPEČNÉ** zastaralé od verze Visual Studio 2015. Definován jako 001 if [/CLR: safe](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;M&#95;FP&#95;EXCEPT** definována jako 1, pokud [/FP: s výjimkou](../build/reference/fp-specify-floating-point-behavior.md) nebo [/FP: strict](../build/reference/fp-specify-floating-point-behavior.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;M&#95;FP&#95;rychlé** definována jako 1, pokud [Fast](../build/reference/fp-specify-floating-point-behavior.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;M&#95;FP&#95;PRECISE** definována jako 1, pokud [/FP: precise](../build/reference/fp-specify-floating-point-behavior.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;M&#95;FP&#95;STRICT** definována jako 1, pokud [/FP: strict](../build/reference/fp-specify-floating-point-behavior.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;M&#95;IX86** definovaný jako celočíselný literál hodnota 600 kompilací této cílové x86 procesory. Toto makro není definován pro x64 nebo kompilace cíle ARM.

- **&#95;M&#95;IX86&#95;FP** definován jako literál celočíselnou hodnotu, která označuje, [/arch](../build/reference/arch-arm.md) – možnost kompilátoru, která byla sada nebo výchozí hodnotu. Toto makro je vždy definováno, pokud jsou cílem kompilaci x x86 procesoru. V opačném případě undefined. Při definování, hodnota je:

  - 0, pokud `/arch:IA32` – možnost kompilátoru byl nastaven.

  - 1, pokud `/arch:SSE` – možnost kompilátoru byl nastaven.

  - Pokud 2 `/arch:SSE2`, `/arch:AVX`, nebo `/arch:AVX2` – možnost kompilátoru byl nastaven. Tato hodnota je výchozí, pokud `/arch` – možnost kompilátoru nebyl zadán. Když `/arch:AVX` není zadána, makro **&#95; &#95;AVX&#95; &#95;** je také definováno. Když `/arch:AVX2` není zadána, obě **&#95; &#95;AVX&#95; &#95;** a **&#95; &#95;AVX2&#95; &#95;** jsou také definovány.

  - Další informace najdete v tématu [/arch (x86)](../build/reference/arch-x86.md).

- **&#95;M&#95;X64** definovaný jako celočíselný literál hodnotu 100 kompilací této cílové x64 procesory. V opačném případě undefined.

- **&#95;SPRAVOVANÉ** definována jako 1, pokud [/CLR](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;MSC&#95;sestavení** definován jako celočíselného literálu, který obsahuje element číslo revize čísla verze kompilátoru. Číslo revize je čtvrtý prvek čísla verze odděleného tečkou. Pokud číslo verze kompilátoru Microsoft C/C++ je 15.00.20706.01, například  **&#95;MSC&#95;sestavení** – makro vyhodnotí na hodnotu 1. Toto makro je vždy definováno.

- **&#95;MSC&#95;rozšíření** definována jako 1, pokud ve výchozím nastavení [/Ze (Povolit jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;MSC&#95;úplné&#95;VER** definován jako literál celého čísla, který kóduje hlavní, podverze a sestavení počet prvků číslo verze kompilátoru. Hlavní číslo je první prvek čísla verze odděleného tečkou, vedlejší číslo je druhý prvek a číslo sestavení je třetí prvek. Pokud číslo verze kompilátoru Microsoft C/C++ je 15.00.20706.01, například  **&#95;MSC&#95;úplné&#95;VER** 150020706 vyhodnotí jako makra. Zadejte `cl /?` příkazového řádku, chcete-li zobrazit číslo verze kompilátoru. Toto makro je vždy definováno.

- **&#95;MSC&#95;VER** definován jako literál celého čísla, který kóduje hlavní a dílčí číslo prvky číslo verze kompilátoru. Hlavní číslo je první prvek čísla verze odděleného tečkou a vedlejší číslo je druhá část. Pokud číslo verze kompilátoru Microsoft C/C++ je 17.00.51106.1, například  **&#95;MSC&#95;VER** – makro vyhodnotí jako 1700. Zadejte `cl /?` příkazového řádku, chcete-li zobrazit číslo verze kompilátoru. Toto makro je vždy definováno.

   |Verze sady Visual Studio|**&#95;MSC&#95;VER**|
   |-|-|
   |Visual Studio 6.0|1200|
   |Visual Studio .NET 2002 (7.0)|1300|
   |Visual Studio .NET 2003 (7.1)|1310|
   |Visual Studio 2005 (8.0)|1400|
   |Visual Studio 2008 (9.0)|1500|
   |Visual Studio 2010 (10.0)|1600|
   |Visual Studio 2012 (11.0)|1700|
   |Visual Studio 2013 (12.0)|1800|
   |Visual Studio 2015 (14.0)|1900|
   |Visual Studio 2017 ve verzi RTW (15.0)|1910|
   |Visual Studio 2017 version 15.3|1911|
   |Visual Studio 2017 verze 15.5|1912|
   |Visual Studio 2017 verze 15.6|1913|
   |Visual Studio 2017 verze 15.7|1914|
   |Visual Studio 2017 verze 15.8|1915|
   |Visual Studio 2017 verze 15.9|1916|
   |Visual Studio RTW 2019 (16.0)|1920|

   K otestování verzemi kompilátoru. nebo aktualizace v dané verzi sady Visual Studio nebo později, použijte **>=** operátor. Vám pomůže ho v podmíněnou direktivu porovnání  **&#95;MSC&#95;VER** proti této známé verze. Pokud máte několik verzí vzájemně se vylučující k porovnání, pořadí vaše porovnání v sestupném pořadí podle čísla verze. Například tento kód kontroluje kompilátory, které jsou všeobecně dostupné v sadě Visual Studio 2017 nebo novější. V dalším kroku kontroluje kompilátory vydané v nebo po sadu Visual Studio 2015. Potom vyhledá všechny kompilátory vydané dřív než Visual Studio 2015:

   ```cpp
   #if _MSC_VER >= 1910
   // . . .
   #elif _MSC_VER >= 1900
   // . . .
   #else
   // . . .
   #endif
   ```

   Další informace najdete v tématu [verze kompilátoru Visual C++](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/) na blogu týmu Microsoft C++.

- **&#95;MSVC&#95;LANG** definován jako celočíselného literálu, který určuje standard jazyka C++, který je cílem kompilátoru. Je nastavena pouze v kódu zkompilovaném jako C++. Celočíselný literál je makro hodnota 201402L ve výchozím nastavení, nebo když [/std: c ++ 14](../build/reference/std-specify-language-standard-version.md) je zadána možnost kompilátoru. Makra je nastavena na 201703L, pokud [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md) je zadána možnost kompilátoru. Je nastavena na hodnotu vyšší, Neurčeno při [/std: c ++ nejnovější](../build/reference/std-specify-language-standard-version.md) je zadána možnost. V opačném případě makro není definováno.  **&#95;MSVC&#95;LANG** – makro a [/STD (určení standardní jazykové verze)](../build/reference/std-specify-language-standard-version.md) jsou k dispozici od verze Visual Studio 2015 Update 3 – možnosti kompilátoru.

- **&#95;&#95;MSVC&#95;RUNTIME&#95;KONTROLUJE** definována jako 1, pokud jeden z [/RTC](../build/reference/rtc-run-time-error-checks.md) nastavit možnosti kompilátoru. V opačném případě undefined.

- **&#95;MT** definována jako 1, pokud [/MD nebo/MDd](../build/reference/md-mt-ld-use-run-time-library.md) (vícevláknové DLL) nebo [/MT nebo/MTD](../build/reference/md-mt-ld-use-run-time-library.md) je zadána (vícevláknové). V opačném případě undefined.

- **&#95;NATIVNÍ&#95;WCHAR&#95;T&#95;definované** definována jako 1, pokud [/Zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;OpenMP –** definované jako celé číslo literálu 200203, pokud [/OpenMP (povolit podporu OpenMP 2.0)](../build/reference/openmp-enable-openmp-2-0-support.md) – možnost kompilátoru je nastavena. Tato hodnota představuje datum specifikace OpenMP implementované ve MSVC. V opačném případě undefined.

   ```cpp
   // _OPENMP_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", _OPENMP);
   }
   ```

- **&#95;Nástroj PREFAST&#95;**  definována jako 1, pokud [/ analyze](../build/reference/analyze-code-analysis.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;&#95;Časové razítko&#95; &#95;**  definovaný jako řetězec literálu, který obsahuje datum a čas poslední změny aktuálního zdrojového souboru, ve formuláři zkrácený, konstantní délka vrácený CRT [asctime –](../c-runtime-library/reference/asctime-wasctime.md) Funkce, například `Fri 19 Aug 13:32:58 2016`. Toto makro je vždy definováno.

- **&#95;VC&#95;NODEFAULTLIB** definována jako 1, pokud [/Zl (vynechat název výchozí knihovny)](../build/reference/zl-omit-default-library-name.md) – možnost kompilátoru je nastavena. V opačném případě undefined.

- **&#95;WCHAR&#95;T&#95;definované** definována jako 1, pokud výchozí [/Zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) – možnost kompilátoru je nastavena.  **&#95;WCHAR&#95;T&#95;definované** – makro je definováno, ale nemá žádnou hodnotu, pokud `/Zc:wchar_t-` – možnost kompilátoru je nastavena, a **wchar_t** je definována v hlavičkovém souboru součástí vaší projekt. V opačném případě undefined.

- **&#95;Win32** definováno jako 1, pokud jsou cílem kompilace ARM 32bitové, 64bitové ARM x86, nebo x 64. V opačném případě undefined.

- **&#95;Win64** definováno jako 1, když je 64-bit ARM nebo x64 cíl kompilace. V opačném případě undefined.

- **&#95;WINRT&#95;DLL** definována jako 1, pokud zkompilovat jako C++ a obě [/ZW (kompilace Windows Runtime)](../build/reference/zw-windows-runtime-compilation.md) a [/LD nebo /LDd](../build/reference/md-mt-ld-use-run-time-library.md) jsou nastavené možnosti kompilátoru. V opačném případě undefined.

Kompilátorem jsou předdefinovány žádné makra preprocesoru, které určují verzi knihovny ATL nebo MFC. Záhlaví knihovny MFC a ATL definice maker tyto verze interně. Se už není definována v direktivách preprocesoru před požadované záhlaví je součástí.

- **&#95;ATL –&#95;VER** definované v \<atldef.h > jako celočíselného literálu, který binárně kóduje ATL číslo verze.

- **&#95;MFC&#95;VER** definované v \<afxver_.h > jako literál celého čísla, který kóduje číslo verze knihovny MFC.

## <a name="see-also"></a>Viz také:

[Makra (C/C++)](../preprocessor/macros-c-cpp.md)<br/>
[Operátory preprocesoru](../preprocessor/preprocessor-operators.md)<br/>
[Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)