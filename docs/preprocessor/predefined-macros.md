---
title: "Předdefinovaná makra | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d938582aad6972573e0d1fc6bddd801ef03307f3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="predefined-macros"></a>Předdefinovaná makra

Visual C++ compiler predefines určité makra preprocesoru, v závislosti na jazyka (C nebo C++), cíl kompilace a možnosti zvolené kompilátoru.

Visual C++ podporuje požadované předdefinovaná preprocesoru makra určeného standardu ANSI/ISO C99 a C ++ 14 standard ISO. Implementace také podporuje několik Další makra preprocesoru specifické pro společnost Microsoft. Některé makra jsou definovány pouze pro prostředí konkrétní sestavení nebo – možnosti kompilátoru. Pokud není uvedeno, makra jsou definovány v rámci překladu jednotky, jako kdyby byly zadány jako **/D** argumenty – možnost kompilátoru. Pokud je definována, jsou makra do zadaných hodnot rozšiřovat preprocesor před kompilace. Předdefinovaná makra nepřebírají žádné argumenty a nelze jej předefinovat.

## <a name="standard-predefined-identifier"></a>Standardní předdefinovaný identifikátor

Kompilátor podporuje tento předdefinované identifikátor určeného ISO C99 a ISO C ++ 11.

- **&#95; &#95; func &#95; &#95;**  Nekvalifikované a prostým název nadřazených funkce jako funkce místní `static const` pole `char`.

    ```cpp
    void example(){
        printf("%s\n", __func__);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>Standardní předdefinovaná makra

Kompilátor podporuje tyto předdefinovaná makra určeného ISO C99 a C ++ 17 normy ISO.

- **&#95; &#95; cplusplus** při kompilaci překladu jednotky jako C++ definované jako celočíselná hodnota literálu. Jinak hodnota není definovaná.

- **&#95; &#95; datum &#95; &#95;**  Datum kompilace aktuální zdrojového souboru. Datum je řetězec délky konstantní literál formuláře *rrrr dd MMMM*. Názvy měsíců *MMMM* je stejný jako název zkrácené měsíce v daty generovanými běhové knihovny jazyka C [asctime –](../c-runtime-library/reference/asctime-wasctime.md) funkce. První znak datum *dd* je místo, pokud je hodnota menší než 10. Toto makro je vždy definováno.

- **&#95; &#95; SOUBOR &#95; &#95;**  Název aktuální zdrojového souboru. **&#95; &#95; SOUBOR &#95; &#95;**  zasahuje do znak řetězcový literál. K zajištění, že se zobrazí úplnou cestu k souboru, použijte [/FC (úplná cesta z souboru zdrojového kódu v diagnostice)](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md). Toto makro je vždy definováno.

- **&#95; &#95; Řádek &#95; &#95;**  Definován jako celé číslo řádku v aktuální zdrojový soubor. Hodnota **&#95; &#95; Řádek &#95; &#95;**  makro lze změnit pomocí `#line` – direktiva. Toto makro je vždy definováno.

- **&#95; &#95; STDC &#95; &#95;**  Definován jako 1, pouze při kompilaci jako C a pokud [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru je zadán. Jinak hodnota není definovaná.

- **&#95; &#95; STDC &#95; HOSTOVANÉ &#95; &#95;**  Definován jako 1, pokud je implementace *hostované implementace*, ten, který podporuje celou požadované standardní knihovnu. Jinak je definován jako 0.

- **&#95; &#95; STDCPP &#95; VLÁKNA &#95; &#95;**  Definován jako 1, pokud program může mít více než jedno vlákno provádění a zkompilovat jako C++. Jinak hodnota není definovaná.

- **&#95; &#95; Čas &#95; &#95;**  Čas posunutí předběžně zpracované překlad jednotky. Čas je řetězec znaků literálu formuláře *hh: mm:*, stejný jako časový vrácený běhové knihovny jazyka C [asctime –](../c-runtime-library/reference/asctime-wasctime.md) funkce. Toto makro je vždy definováno.

## <a name="microsoft-specific-predefined-macros"></a>Předdefinovaná makra specifické pro společnost Microsoft

Microsoft Visual C++ podporuje tyto další předdefinovaná makra.

- **&#95; &#95; ATOM &#95; &#95;**  Definován jako v případě 1 [/favor:ATOM](../build/reference/favor-optimize-for-architecture-specifics.md) – možnost kompilátoru a je nastaven cíl kompilátoru x86 nebo x64. Jinak hodnota není definovaná.

- **&#95; &#95; AVX &#95; &#95;**  Definován jako v případě 1 [/arch:AVX](../build/reference/arch-x86.md) nebo [/arch:AVX2](../build/reference/arch-x86.md) nastavení možností kompilátoru a cíl kompilátoru se x86 nebo x64. Jinak hodnota není definovaná.

- **&#95; &#95; AVX2 &#95; &#95;**  Definován jako v případě 1 [/arch:AVX2](../build/reference/arch-x86.md) – možnost kompilátoru a je nastaven cíl kompilátoru x86 nebo x64. Jinak hodnota není definovaná.

- **&#95; CHAR &#95; NEPODEPSANÉ** definované jako 1-li výchozí `char` typ není podepsán. To je nastavena, když [/J (výchozí znakový typ není podepsán)](../build/reference/j-default-char-type-is-unsigned.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

- **&#95; &#95; CLR &#95; VER** definován jako literál celé číslo, které představuje verzi modul common language runtime používá při kompilace aplikace. Hodnota je zakódován do formátu `Mmmbbbbb`, kde `M` je hlavní verzi modulu runtime `mm` je vedlejší verzi modulu runtime a `bbbbb` je číslo sestavení. **&#95; &#95; CLR &#95; VER** je definována, pokud [/CLR](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(__CLR_VER);
    }
    ```

- **&#95; Ovládací PRVEK &#95; TOK &#95; Ochrana** definován jako v případě 1 [/guard:cf (povolení ochrany toku řízení)](../build/reference/guard-enable-control-flow-guard.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

- **&#95; &#95; Čítač &#95; &#95;**  Expands na celé číslo literál, který začíná na 0 a se zvýší o 1 pokaždé, když se používá ve zdrojovém souboru nebo zahrnuté hlavičky zdrojového souboru. **&#95; &#95; Čítač &#95; &#95;**  pamatuje jejím stavu, při použití předkompilovaných hlaviček. Toto makro je vždy definováno.

  Tento příklad používá `__COUNTER__` přiřadit jedinečné identifikátory pro tři různé objekty stejného typu. `exampleClass` Konstruktor trvá celé jako parametr. V `main`, aplikace deklaruje tři objekty typu `exampleClass`pomocí `__COUNTER__` jako jedinečný identifikátor parametr:

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

- **&#95; &#95; cplusplus &#95; cli** definován jako celé číslo literálovou hodnotou 200406 při kompilaci jako C++ a [/CLR](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná. Při definování, **&#95; &#95; cplusplus &#95; cli** platí v celé jednotky překladu.

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

- **&#95; &#95; cplusplus &#95; winrt** definován jako celé číslo literálovou hodnotou 201009 při kompilaci jako C++ a [/ZW (kompilace Windows Runtime)](../build/reference/zw-windows-runtime-compilation.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

- **&#95; CPPRTTI** definované jako 1-li [/GR (Povolit Run-Time informace typu)](../build/reference/gr-enable-run-time-type-information.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

- **&#95; CPPUNWIND** definován jako 1, pokud jeden nebo více [/GX (povolení zpracování výjimek)](../build/reference/gx-enable-exception-handling.md), [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md), nebo [/EH (výjimka zpracování modelu)](../build/reference/eh-exception-handling-model.md) nastavení možností kompilátoru. Jinak hodnota není definovaná.

- **&#95; ladění** definován jako v případě 1 [/LDd](../build/reference/md-mt-ld-use-run-time-library.md), [/MDd](../build/reference/md-mt-ld-use-run-time-library.md), nebo [/MTd](../build/reference/md-mt-ld-use-run-time-library.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

- **&#95; DLL** definován jako v případě 1 [/MD](../build/reference/md-mt-ld-use-run-time-library.md) nebo [/MDd](../build/reference/md-mt-ld-use-run-time-library.md) – možnost kompilátoru (vícevláknových knihoven DLL) je nastaven. Jinak hodnota není definovaná.

- **&#95; &#95; FUNCDNAME &#95; &#95;**  Definován jako řetězcový literál, který obsahuje [dekorované název](../build/reference/decorated-names.md) nadřazených funkce. Makro je definována pouze v rámci funkce. **&#95; &#95; FUNCDNAME &#95; &#95;**  makro není rozbalen, pokud použijete [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) nebo [/P](../build/reference/p-preprocess-to-a-file.md) – možnost kompilátoru.

   Tento příklad používá `__FUNCDNAME__`, `__FUNCSIG__`, a `__FUNCTION__` makra pro zobrazení informací funkce.

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- **&#95; &#95; FUNCSIG &#95; &#95;**  Definován jako řetězcový literál, který obsahuje podpis nadřazených funkce. Makro je definována pouze v rámci funkce. **&#95; &#95; FUNCSIG &#95; &#95;**  makro není rozbalen, pokud použijete [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) nebo [/P](../build/reference/p-preprocess-to-a-file.md) – možnost kompilátoru. Při kompilaci pro 64bitové cílové, konvence volání je `__cdecl` ve výchozím nastavení. Příklad použití, naleznete v části `__FUNCDNAME__` makro.

- **&#95; &#95; Funkce &#95; &#95;**  Definován jako řetězcový literál, který obsahuje název bez upraveného nadřazených funkce. Makro je definována pouze v rámci funkce. **&#95; &#95; Funkce &#95; &#95;**  makro není rozbalen, pokud použijete [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) nebo [/P](../build/reference/p-preprocess-to-a-file.md) – možnost kompilátoru. Příklad použití, naleznete v části `__FUNCDNAME__` makro.

- **&#95; INTEGRÁLNÍ &#95; Maximální počet &#95; Služba BITS** definovaná jako literál celočíselnou hodnotu 64, maximální velikost (v bits) pro typ integrální bez vektoru. Toto makro je vždy definováno.

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", _INTEGRAL_MAX_BITS);
   }
   ```

- **&#95; &#95; INTELLISENSE &#95; &#95;**  Definován jako předat 1 během kompilátoru IntelliSense v prostředí Visual Studio IDE. Jinak hodnota není definovaná. Můžete použít tento makro ochrana kódu technologie IntelliSense kompilátoru nemá pochopit, nebo použít k přepnutí mezi sestavení a kompilátoru IntelliSense. Další informace najdete v tématu [řešení potíží s tipy pro IntelliSense pomalost](https://blogs.msdn.microsoft.com/vcblog/2011/03/29/troubleshooting-tips-for-intellisense-slowness/).

- **&#95; ISO &#95; VOLATILE** definované jako 1-li [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

- **&#95; JÁDRA &#95; REŽIM** definované jako 1-li [/Kernel (vytvoření binárního režimu jádra)](../build/reference/kernel-create-kernel-mode-binary.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

- **&#95; M &#95; AMD64** definován jako celé číslo literálu hodnotu 100 kompilací tento cíl x64 procesory. Jinak hodnota není definovaná.

- **&#95; M &#95; ARM** definován jako literál celočíselnou hodnotu 7 kompilací, které cílí procesory ARM. Jinak hodnota není definovaná.

- **&#95; M &#95; ARM &#95; ARMV7VE** definován jako v případě 1 [/arch:ARMv7VE](../build/reference/arch-arm.md) – možnost kompilátoru nastavena kompilací, které cílí procesory ARM. Jinak hodnota není definovaná.

- **&#95; M &#95; ARM &#95; FP** definován jako literál celočíselná hodnota, která označuje, které [/arch](../build/reference/arch-arm.md) – možnost kompilátoru byla nastavena, je-li cílové kompilace procesor ARM. Jinak hodnota není definovaná.

  - V rozsahu 30 39 Pokud žádné **/arch** byla zadána možnost ARM, označující výchozí architekturu pro ARM byl nastaven (`VFPv3`).

  - V rozsahu 40 49 Pokud **/arch:VFPv4** byl nastaven.

  - V tématu [/arch (ARM)](../build/reference/arch-arm.md) Další informace.

- **&#95; M &#95; ARM64** definován jako 1 kompilací, které cílí 64bitovými procesory ARM. Jinak hodnota není definovaná.

- **&#95; M &#95; CEE** definované jako 001-li žádné [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

- **&#95; M &#95; CEE &#95; ČISTÝ** zastaralé od verze sady Visual Studio 2015. Definované jako 001-li [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md) nastavena – možnost kompilátoru. Jinak hodnota není definovaná.

- **&#95; M &#95; CEE &#95; BEZPEČNÉ** zastaralé od verze sady Visual Studio 2015. Definované jako 001-li [/CLR: safe](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

- **&#95; M &#95; FP &#95; S výjimkou** definované jako 1-li [/fp: kromě](../build/reference/fp-specify-floating-point-behavior.md) nebo [/fp: striktní](../build/reference/fp-specify-floating-point-behavior.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

- **&#95; M &#95; FP &#95; Rychlé** definované jako 1-li [/fp:fast](../build/reference/fp-specify-floating-point-behavior.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

- **&#95; M &#95; FP &#95; PŘESNÉ** definované jako 1-li [/fp: přesné](../build/reference/fp-specify-floating-point-behavior.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

- **&#95; M &#95; FP &#95; STRIKTNÍ** definované jako 1-li [/fp: striktní](../build/reference/fp-specify-floating-point-behavior.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

- **&#95; M &#95; IX86** definován jako celé číslo literálu hodnotu 600 kompilací tento cíl x86 procesory. Toto makro není definován pro x64 nebo ARM kompilace cíle.

- **&#95; M &#95; IX86 &#95; FP** definován jako literál celočíselná hodnota, která určuje, [/arch](../build/reference/arch-arm.md) – možnost kompilátoru sady nebo výchozí. Tato – makro je vždy definována, pokud jsou cílem kompilace x86 procesoru. Jinak hodnota není definovaná. Pokud je definována, hodnota je:

  - 0, pokud **/arch:IA32** – možnost kompilátoru byl nastaven.

  - v případě 1 **/arch:SSE** – možnost kompilátoru byl nastaven.

  - v případě 2 **/arch:SSE2**, **/arch:AVX** nebo **/arch:AVX2** – možnost kompilátoru byl nastaven. Tato hodnota je výchozí, pokud **/arch** – možnost kompilátoru nebyl zadán. Když **/arch:AVX** není zadaný, makro **&#95; &#95; AVX &#95; &#95;**  je také definován. Když **/arch:AVX2** není zadaný, obě **&#95; &#95; AVX &#95; &#95;**  a **&#95; &#95; AVX2 &#95; &#95;**  , je definována.

  - V tématu [/arch (x86)](../build/reference/arch-x86.md) Další informace.

- **&#95; M &#95; X64** definován jako celé číslo literálu hodnotu 100 kompilací tento cíl x64 procesory. Jinak hodnota není definovaná.

- **&#95; SPRAVOVANÉ** definován jako v případě 1 [/CLR](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

- **&#95; MSC &#95; SESTAVENÍ** definován jako celé číslo literál, který obsahuje element číslo revize čísla verze kompilátoru. Číslo revize se čtvrtý elementu číslo verze tečkou. Pokud je číslo verze Visual C++ compiler 15.00.20706.01, například **&#95; MSC &#95; SESTAVENÍ** makro vyhodnotí na 1. Toto makro je vždy definováno.

- **&#95; MSC &#95; ROZŠÍŘENÍ** definované jako 1-li [/Ze (Povolit jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru je nastavena, což je výchozí hodnota. Jinak hodnota není definovaná.

- **&#95; MSC &#95; ÚPLNÉ &#95; VER** definovaný jako literál celé číslo, které kóduje hlavní, malé a počet prvků kompilátoru číslo verze sestavení. Hlavní číslo je první prvek číslo verze tečkou, druhý prvkem je menší počet a číslo sestavení je třetí elementu. Pokud je číslo verze Visual C++ compiler 15.00.20706.01, například **&#95; MSC &#95; ÚPLNÉ &#95; VER** makro vyhodnocen jako 150020706. Zadejte **cl /?** na příkazovém řádku zobrazíte kompilátoru číslo verze. Toto makro je vždy definováno.

- **&#95; MSC &#95; VER** definován jako literál celé číslo, které kóduje hlavní a podverze počet prvků kompilátoru číslo verze. Hlavní číslo je první prvek číslo verze tečkou a druhý prvkem je menší číslo. Pokud je číslo verze Visual C++ compiler 17.00.51106.1, například **&#95; MSC &#95; VER** makro vyhodnocen jako 1 700. Zadejte **cl /?** na příkazovém řádku zobrazíte kompilátoru číslo verze. Toto makro je vždy definováno.

- **&#95; MSVC &#95; JAZYK** definován jako literál celé číslo, které určuje cílem kompilátor standardní jazyka C++. Při kompilaci jako C++, makro je literálovou hodnotou 201402L celé číslo, pokud [/std: c ++ 14](../build/reference/std-specify-language-standard-version.md) – možnost kompilátoru není nastaven, nebo ve výchozím nastavení; jinak je nastavená na 201703 L Pokud [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md) – možnost kompilátoru nastavena; a je nastaven na hodnotu vyšší, Neurčeno hodnotu v případě [/std: c ++ nejnovější](../build/reference/std-specify-language-standard-version.md). Makro, jinak hodnota není definován. **&#95; MSVC &#95; JAZYK** makro a [/std (zadejte jazyk standardní verze)](../build/reference/std-specify-language-standard-version.md) – možnosti kompilátoru jsou k dispozici od verze Visual Studio 2015 Update 3.

- **&#95; &#95; MSVC &#95; Modul RUNTIME &#95; KONTROLUJE** definován jako 1, pokud jeden z [/RTC](../build/reference/rtc-run-time-error-checks.md) – možnosti kompilátoru nastavena. Jinak hodnota není definovaná.

- **&#95; MT** definován jako v případě 1 [/MD nebo /MDd](../build/reference/md-mt-ld-use-run-time-library.md) (s více vlákny DLL) nebo [/MT nebo /MTd](../build/reference/md-mt-ld-use-run-time-library.md) (Multithreaded) je zadán. Jinak hodnota není definovaná.

- **&#95; NATIVNÍ &#95; WCHAR &#95; T &#95; DEFINOVANÁ** definován jako v případě 1 [/Zc:](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

- **&#95; OPENMP** definován jako celé číslo literálu 200203 představující datum specifikace OpenMP implementováno modulem Visual C++, pokud [/OpenMP (povolit podporu OpenMP 2.0)](../build/reference/openmp-enable-openmp-2-0-support.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

   ```cpp
   // _OPENMP_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", _OPENMP);
   }
   ```

- **&#95; Nástroj PREFAST &#95;**  Definován jako v případě 1 [/ analyze](../build/reference/analyze-code-analysis.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

- **&#95; &#95; Časové razítko &#95; &#95;**  Definován jako řetězcový literál, který obsahuje datum a čas poslední změny aktuální zdrojového souboru ve formátu zkrácené, konstantní délka vrácený běhové knihovny jazyka C [asctime –](../c-runtime-library/reference/asctime-wasctime.md) funkce, například `Fri 19 Aug 13:32:58 2016`. Toto makro je vždy definováno.

- **&#95; VC &#95; NODEFAULTLIB** definován jako v případě 1 [/Zl (vypuštění název výchozí knihovny)](../build/reference/zl-omit-default-library-name.md) – možnost kompilátoru nastavena. Jinak hodnota není definovaná.

- **&#95; WCHAR &#95; T &#95; DEFINOVANÁ** definován jako 1 v případě výchozí [/Zc:](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) – možnost kompilátoru nastavena. **&#95; WCHAR &#95; T &#95; DEFINOVANÁ** makro je definován, ale nemá žádnou hodnotu, pokud **/Zc:wchar_t-** – možnost kompilátoru nastavena, a `wchar_t` je definován v záhlaví souboru systému součástí projektu. Jinak hodnota není definovaná.

- **&#95; Win32** definovaná jako 1, pokud jsou cílem kompilace ARM 32bitové, 64bitové ARM x86, nebo x 64. Jinak hodnota není definovaná.

- **&#95; Win64** definován jako 1, pokud jsou cílem kompilace ARM 64-bit nebo x64. Jinak hodnota není definovaná.

- **&#95; WINRT &#95; DLL** definované jako v případě 1 zkompilovat jako C++ a obě [/ZW (kompilace Windows Runtime)](../build/reference/zw-windows-runtime-compilation.md) a [/LD nebo /LDd](../build/reference/md-mt-ld-use-run-time-library.md) nastavení možností kompilátoru. Jinak hodnota není definovaná.

 Makra preprocesoru používá k určení verze knihovny ATL nebo MFC nejsou předdefinované kompilátorem. Tyto makra jsou definovány v hlavičkách knihovny, tak nejsou definovaná v preprocesor – direktivy předtím, než je zahrnuté požadovaná hlavička.

- **&#95; ATL &#95; VER** definované v \<atldef.h > jako literál celé číslo, které kóduje ATL číslo verze.

- **&#95; MFC &#95; VER** definované v \<afxver_.h > jako literál celé číslo, které kóduje MFC číslo verze.

## <a name="see-also"></a>Viz také

[Makra (C/C++)](../preprocessor/macros-c-cpp.md)   
[Operátory preprocesoru](../preprocessor/preprocessor-operators.md)   
[Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)
