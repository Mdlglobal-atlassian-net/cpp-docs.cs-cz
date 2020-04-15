---
title: 'C++ Build Insights SDK: tabulka událostí'
description: Odkaz na událost pro sdk sestavení sady Visual Studio C++
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Events
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 932b78347e05d313e7962da2fdff8c3454dec963
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324144"
---
# <a name="c-build-insights-sdk-event-table"></a>C++ Build Insights SDK: tabulka událostí

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

## <a name="compiler-events"></a>Události kompilátoru

[Kompilátoru](#compiler)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[OBJ_OUTPUT](#obj-output)\
[FRONT_END_PASS](#front-end-pass)\
[BACK_END_PASS](#back-end-pass)

## <a name="compiler-front-end-events"></a>Události front-endu kompilátoru

[C1_DLL](#c1-dll)\
[FRONT_END_FILE](#front-end-file)\
[TEMPLATE_INSTANTIATION](#template-instantiation)\
[SYMBOL_NAME](#symbol-name)

## <a name="compiler-back-end-events"></a>Události back-endu kompilátoru

[C2_DLL](#c2-dll)\
[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis)\
[TOP_DOWN](#top-down)\
[BOTTOM_UP](#bottom-up)\
[CODE_GENERATION](#code-generation)\
[Vlákno](#thread)\
[Funkce](#function)\
[FORCE_INLINEE](#force-inlinee)

## <a name="linker-events"></a>Události linkeru

[Linker](#linker)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)\
[EXP_OUTPUT](#exp-output)\
[IMP_LIB_OUTPUT](#imp-lib-output)\
[LIB_OUTPUT](#lib-output)\
[PRŮKAZ 1](#pass1)\
[PRE_LTCG_OPT_REF](#pre-ltcg-opt-ref)\
[LTCG](#ltcg)\
[OPT_REF](#opt-ref)\
[OPT_ICF](#opt-icf)\
[OPT_LBR](#opt-lbr)\
[PRŮKAZ 2](#pass2)

## <a name="event-table"></a>Tabulka událostí

| Událost | Vlastnost | Popis |
|--|--|--|
| <a name="back-end-pass"></a>BACK_END_PASS | Typ | Aktivita |
|  | Nadřazené prvky | [Kompilátoru](#compiler) |
|  | Podřízené prvky | [C2_DLL](#c2-dll) |
|  | Vlastnosti | - Absolutní cesta k vstupnímu zdrojovému souboru<br/>- Absolutní cesta k výstupnímu souboru objektu |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[KompilátorPass](cpp-event-data-types/compiler-pass.md)<br/>[Backendpass](cpp-event-data-types/back-end-pass.md) |
|  | Popis | Vyskytuje se na začátku a zastavení back-endprůchodu kompilátoru. Tento průchod je zodpovědný za optimalizaci analyzovaného zdrojového kódu C/C++ a jeho převod na strojový kód. |
| <a name="bottom-up"></a>BOTTOM_UP | Typ | Aktivita |
|  | Nadřazené prvky | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Podřízené prvky | Žádný |
|  | Vlastnosti | Žádný |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[Dole nahoru](cpp-event-data-types/bottom-up.md) |
|  | Popis | Vyskytuje se na začátku a zastavení průchodu celé analýzy programu zdola nahoru. |
| <a name="c1-dll"></a>C1_DLL | Typ | Aktivita |
|  | Nadřazené prvky | [FRONT_END_PASS](#front-end-pass) |
|  | Podřízené prvky | [FRONT_END_FILE](#front-end-file)<br/>[SYMBOL_NAME](#symbol-name)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Vlastnosti | Žádný |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[C1DLL](cpp-event-data-types/c1-dll.md) |
|  | Popis | Vyvolá ní na začátku a na začátku a při vyvolání *souboru c1.dll* nebo *c1xx.dll.* Tyto knihovny DLL jsou předchůdky c a c++ kompilátoru. Jsou vyvolány výhradně ovladačem kompilátoru *(cl.exe).* |
| <a name="c2-dll"></a>C2_DLL | Typ | Aktivita |
|  | Nadřazené prvky | [BACK_END_PASS](#back-end-pass)<br/>[LTCG](#ltcg) |
|  | Podřízené prvky | [CODE_GENERATION](#code-generation)<br/>[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Vlastnosti | Žádný |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[C2DLL](cpp-event-data-types/c2-dll.md) |
|  | Popis | Vyvolá ní na začátku a v důsledku vyvolání *souboru c2.dll.* Tato dll je zadní konec kompilátoru. Je volána ovladačem kompilátoru *(cl.exe).* Je také vyvolána linker (*link.exe*) při generování kódu v době propojení. |
| <a name="code-generation"></a>CODE_GENERATION | Typ | Aktivita |
|  | Nadřazené prvky | [C2_DLL](#c2-dll) |
|  | Podřízené prvky | [Funkce](#function)<br/>[Vlákno](#thread) |
|  | Vlastnosti | Žádný |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[Generování kódu](cpp-event-data-types/code-generation.md) |
|  | Popis | Vyskytuje se na začátku a zastavení fáze generování kódu back-endu. |
| <a name="command-line"></a>COMMAND_LINE | Typ | Jednoduchá událost |
|  | Nadřazené prvky | [Kompilátoru](#compiler)<br/>[Linker](#linker) |
|  | Podřízené prvky | Žádný |
|  | Vlastnosti | - Příkazový řádek, který byl použit k vyvolání *cl.exe* nebo *link.exe* |
|  | Zachytávání tříd | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Commandline](cpp-event-data-types/command-line.md) |
|  | Popis | Vyvolá se, když kompilátor a propojovací programu jsou hotové vyhodnocení příkazového řádku. Vyhodnocený příkazový řádek obsahuje všechny parametry *cl.exe* a *link.exe* předané prostřednictvím souboru odpovědí. Obsahuje také parametry *cl.exe* a *link.exe* předané prostřednictvím \_\_proměnných prostředí, jako jsou CL, CL , LINK a \_LINK\_. |
| <a name="compiler"></a>Kompilátoru | Typ | Aktivita |
|  | Nadřazené prvky | Žádný |
|  | Podřízené prvky | [BACK_END_PASS](#back-end-pass)<br/>[COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[FILE_INPUT](#file-input)<br/>[OBJ_OUTPUT](#obj-output)<br/>[FRONT_END_PASS](#front-end-pass) |
|  | Vlastnosti | - Verze kompilátoru<br/>- Pracovní adresář<br/>- Absolutní cesta k vyvolaný *cl.exe* |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[Vyvolání](cpp-event-data-types/invocation.md)<br/>[Kompilátoru](cpp-event-data-types/compiler.md) |
|  | Popis | Vyskytuje se na začátku a zastavení *vyvolání cl.exe.* |
| <a name="environment-variable"></a>ENVIRONMENT_VARIABLE | Typ | Jednoduchá událost |
|  | Nadřazené prvky | [Kompilátoru](#compiler)<br/>[Linker](#linker) |
|  | Podřízené prvky | Žádný |
|  | Vlastnosti | - Název proměnné prostředí<br/>- Hodnota proměnné prostředí. |
|  | Zachytávání tříd | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Proměnná prostředí](cpp-event-data-types/environment-variable.md) |
|  | Popis | Vyvolá se jednou pro každou existující proměnnou prostředí v době, kdy je vyvolána *cl.exe* nebo *link.exe.* |
| <a name="executable-image-output"></a>EXECUTABLE_IMAGE_OUTPUT | Typ | Jednoduchá událost |
|  | Nadřazené prvky | [Linker](#linker) |
|  | Podřízené prvky | Žádný |
|  | Vlastnosti | - Absolutní cesta k dll nebo spustitelný výstupní soubor. |
|  | Zachytávání tříd | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Výstup souboru](cpp-event-data-types/file-output.md)<br/>[Spustitelný výstup ImageOutput](cpp-event-data-types/executable-image-output.md) |
|  | Popis | Vyvolá se, když je jedním ze vstupů propojovacího systému dll nebo spustitelný obrazový soubor. |
| <a name="exp-output"></a>EXP_OUTPUT | Typ | Jednoduchá událost |
|  | Nadřazené prvky | [Linker](#linker) |
|  | Podřízené prvky | Žádný |
|  | Vlastnosti | - Absolutní cesta k výstupnímu souboru *EXP.* |
|  | Zachytávání tříd | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Výstup souboru](cpp-event-data-types/file-output.md)<br/>[ExpOutput](cpp-event-data-types/exp-output.md) |
|  | Popis | Vyvolá se v případě, že jeden z výstupů propojovacího zařízení je soubor *EXP.* |
| <a name="file-input"></a>FILE_INPUT | Typ | Jednoduchá událost |
|  | Nadřazené prvky | [Kompilátoru](#compiler)<br/>[Linker](#linker) |
|  | Podřízené prvky | Žádný |
|  | Vlastnosti | - Absolutní cesta ke vstupnímu souboru<br/>- Typ vstupního souboru |
|  | Zachytávání tříd | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileInput](cpp-event-data-types/file-input.md) |
|  | Popis | Vyvolá oznámení vstupu *cl.exe* nebo *link.exe.* |
| <a name="force-inlinee"></a>FORCE_INLINEE | Typ | Jednoduchá událost |
|  | Nadřazené prvky | [Funkce](#function) |
|  | Podřízené prvky | Žádný |
|  | Vlastnosti | - Název funkce vložené silou.<br/>- Velikost funkce vložené silou, reprezentované jako počet zprostředkujícíinstrukce. |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[SílaInlinee](cpp-event-data-types/force-inlinee.md) |
|  | Popis | Vyvolá se, když je funkce vsazena do `__forceinline` jiné funkce pomocí klíčového slova. |
| <a name="front-end-file"></a>FRONT_END_FILE | Typ | Aktivita |
|  | Nadřazené prvky | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file) |
|  | Podřízené prvky | [FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Vlastnosti | - Absolutní cesta k souboru. |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[Soubor frontendů](cpp-event-data-types/front-end-file.md) |
|  | Popis | Vyvolá se při spuštění front-endu kompilátoru a zastaví zpracování souboru. Tato událost je rekurzivní. Rekurze se stane, když front-end je analýza zahrnuté soubory. |
| <a name="front-end-pass"></a>FRONT_END_PASS | Typ | Aktivita |
|  | Nadřazené prvky | [Kompilátoru](#compiler) |
|  | Podřízené prvky | [C1_DLL](#c1-dll) |
|  | Vlastnosti | - Absolutní cesta k vstupnímu zdrojovému souboru<br/>- Absolutní cesta k výstupnímu souboru objektu |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[KompilátorPass](cpp-event-data-types/compiler-pass.md)<br/>[Frontendpass](cpp-event-data-types/front-end-pass.md) |
|  | Popis | Vyvolá se na začátku a zastavení front-endu kompilátoru. Tento průchod je zodpovědný za analýzu zdrojového kódu C/C++ a jeho převod do zprostředkujícího jazyka. |
| <a name="function"></a>Funkce | Typ | Aktivita |
|  | Nadřazené prvky | [CODE_GENERATION](#code-generation)<br/>[Vlákno](#thread)<br/>[TOP_DOWN](#top-down) |
|  | Podřízené prvky | [FORCE_INLINEE](#force-inlinee) |
|  | Vlastnosti | - Název funkce |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[Funkce](cpp-event-data-types/function.md) |
|  | Popis | Vyvolá se při spuštění a ukončení generování kódu funkce. |
| <a name="imp-lib-output"></a>IMP_LIB_OUTPUT | Typ | Jednoduchá událost |
|  | Nadřazené prvky | [Linker](#linker) |
|  | Podřízené prvky | Žádný |
|  | Vlastnosti | - Absolutní cesta k výstupnímu souboru importu knihovny. |
|  | Zachytávání tříd | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Výstup souboru](cpp-event-data-types/file-output.md)<br/>[ImpLibVýstup](cpp-event-data-types/imp-lib-output.md) |
|  | Popis | Vyvolá se, když jeden z výstupů propojovacího zařízení je knihovna importu. |
| <a name="lib-output"></a>LIB_OUTPUT | Typ | Jednoduchá událost |
|  | Nadřazené prvky | [Linker](#linker) |
|  | Podřízené prvky | Žádný |
|  | Vlastnosti | - Absolutní cesta k statické knihovně výstupní soubor. |
|  | Zachytávání tříd | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Výstup souboru](cpp-event-data-types/file-output.md)<br/>[LibOutput](cpp-event-data-types/lib-output.md) |
|  | Popis | Vyvolá se, když jeden z výstupů propojovacího zařízení je statická knihovna. |
| <a name="linker"></a>Linker | Typ | Aktivita |
|  | Nadřazené prvky | Žádný |
|  | Podřízené prvky | [COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)<br/>[EXP_OUTPUT](#exp-output)<br/>[FILE_INPUT](#file-input)<br/>[IMP_LIB_OUTPUT](#imp-lib-output)<br/>[LIB_OUTPUT](#lib-output)<br/>[PRŮKAZ 1](#pass1)<br/>[PRŮKAZ 2](#pass2) |
|  | Vlastnosti | - Linker verze<br/>- Pracovní adresář<br/>- Absolutní cesta k vyvolaný *link.exe* |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[Vyvolání](cpp-event-data-types/invocation.md)<br/>[Linker](cpp-event-data-types/linker.md) |
|  | Popis | Vyvolá na začátku a zazastavení vyvolání *souboru link.exe.* |
| <a name="ltcg"></a>LTCG | Typ | Aktivita |
|  | Nadřazené prvky | [PRŮKAZ 1](#pass1) |
|  | Podřízené prvky | [C2_DLL](#c2-dll) |
|  | Vlastnosti | Žádný |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[LTCG](cpp-event-data-types/ltcg.md) |
|  | Popis | Vyvolá se na začátku a zastavení generování kódu v době propojení. |
| <a name="obj-output"></a>OBJ_OUTPUT | Typ | Jednoduchá událost |
|  | Nadřazené prvky | [Kompilátoru](#compiler) |
|  | Podřízené prvky | Žádný |
|  | Vlastnosti | - Absolutní cesta k výstupnímu souboru *OBJ* |
|  | Zachytávání tříd | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Výstup souboru](cpp-event-data-types/file-output.md)<br/>[ObjVýstup](cpp-event-data-types/obj-output.md) |
|  | Popis | Vyskytuje se jednou pro každý výstup *.obj* produkovaný *cl.exe*. |
| <a name="opt-icf"></a>OPT_ICF | Typ | Aktivita |
|  | Nadřazené prvky | [PRŮKAZ 1](#pass1) |
|  | Podřízené prvky | Žádný |
|  | Vlastnosti | Žádný |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[OptiCF](cpp-event-data-types/opt-icf.md) |
|  | Popis | Vyvolá se na začátku a zastavení identické optimalizace propojovacího programu COMDAT (/OPT:ICF). |
| <a name="opt-lbr"></a>OPT_LBR | Typ | Aktivita |
|  | Nadřazené prvky | [PRŮKAZ 1](#pass1) |
|  | Podřízené prvky | Žádný |
|  | Vlastnosti | Žádný |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[OptLBR](cpp-event-data-types/opt-lbr.md) |
|  | Popis | Vyvolá se při spuštění a zastavení optimalizace propojovacího programu dlouhé větve (/OPT:LBR). |
| <a name="opt-ref"></a>OPT_REF | Typ | Aktivita |
|  | Nadřazené prvky | [PRŮKAZ 1](#pass1) |
|  | Podřízené prvky | Žádný |
|  | Vlastnosti | Žádný |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[OptRef](cpp-event-data-types/opt-ref.md) |
|  | Popis | Vyvolá se při spuštění a zastavení neodkazovaných funkcí a optimalizace propojovacího programu (/OPT:REF). |
| <a name="pass1"></a>PRŮKAZ 1 | Typ | Aktivita |
|  | Nadřazené prvky | [Linker](#linker) |
|  | Podřízené prvky | [LTCG](#ltcg)<br/>[OPT_ICF](#opt-icf)<br/>[OPT_LBR](#opt-lbr)<br/>[OPT_REF](#opt-ref) |
|  | Vlastnosti | Žádný |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[Průchod1](cpp-event-data-types/pass1.md) |
|  | Popis | Vyvolá se na začátku a zastavení průchodu linkeru 1. |
| <a name="pass2"></a>PRŮKAZ 2 | Typ | Aktivita |
|  | Nadřazené prvky | [Linker](#linker) |
|  | Podřízené prvky | Žádný |
|  | Vlastnosti | Žádný |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[Průchod2](cpp-event-data-types/pass2.md) |
|  | Popis | Vyvolá se na začátku a zastavení průchodu propojovacího nebo spoje 2. |
| <a name="pre-ltcg-opt-ref"></a>PRE_LTCG_OPT_REF | Typ | Aktivita |
|  | Nadřazené prvky | [PRŮKAZ 1](#pass1) |
|  | Podřízené prvky | Žádný |
|  | Vlastnosti | Žádný |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[Program PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md) |
|  | Popis | Vyvolá se při spuštění a zastavení průchodu optimalizace propojovacího programu, který eliminuje neodkazované funkce a data (/OPT:REF). To se provádí před generováním kódu v době propojení. |
| <a name="symbol-name"></a>SYMBOL_NAME | Typ | Jednoduchá událost |
|  | Nadřazené prvky | [C1_DLL](#c1-dll) |
|  | Podřízené prvky | Žádný |
|  | Vlastnosti | - Typový klíč<br/> - Název typu |
|  | Zachytávání tříd | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Název_symbolu](cpp-event-data-types/symbol-name.md) |
|  | Popis | Vyskytuje se na konci front-end průchodu: jednou pro každý typ zapojený do vytváření instancí šablony. Klíč je číselný identifikátor pro typ, zatímco název je jeho text reprezentace. Klíče typu jsou jedinečné v rámci trasování, které se analyzuje. Různé klíče pocházející z různých průchodů front-endkompilátoru však mohou ukazovat na stejný typ. Porovnání typů mezi různými front-endovými průchody kompilátoru vyžaduje použití jejich názvů. SYMBOL_NAME události jsou vydávány na konci front-endu kompilátoru, po všechny instance šablony. |
| <a name="template-instantiation"></a>TEMPLATE_INSTANTIATION | Typ | Aktivita |
|  | Nadřazené prvky | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Podřízené prvky | [TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Vlastnosti | - Klíč pro specializovaný typ<br/>- Klíč pro typ primární šablony<br/>- Druh šablony, která byla vytvořena |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[ŠablonaVytvoření](cpp-event-data-types/template-instantiation.md) |
|  | Popis | Vyvolá se na začátku a na konci instance šablony. Instance primárního typu `vector`šablony (například ) má za následek specializovaný typ `std::vector<int>`(například ). Klíč je uveden pro oba typy. Pomocí [SYMBOL_NAME](#symbol-name) události převeďte klíč na název typu. Klíče typu jsou jedinečné v rámci trasování, které se analyzuje. Různé klíče pocházející z různých průchodů front-endkompilátoru však mohou ukazovat na stejný typ. Porovnání typů mezi různými front-endovými průchody kompilátoru vyžaduje použití názvů symbolů. Tato událost je rekurzivní. Rekurze se stane v některých případech, kdy front-end je vytváření instancí vnořené šablony. |
| <a name="thread"></a>Vlákno | Typ | Aktivita |
|  | Nadřazené prvky | [CODE_GENERATION](#code-generation)<br/>[TOP_DOWN](#top-down) |
|  | Podřízené prvky | [Funkce](#function) |
|  | Vlastnosti | Žádný |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[Vlákno](cpp-event-data-types/thread.md) |
|  | Popis | Vyvolá se na začátku a na konci spuštění podprocesu back-endu kompilátoru. Pozastavené vlákno je považováno za ukončené. Vlákno, které se probouzí, je považováno za spuštěné. |
| <a name="top-down"></a>TOP_DOWN | Typ | Aktivita |
|  | Nadřazené prvky | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Podřízené prvky | [Funkce](#function)<br/>[Vlákno](#thread) |
|  | Vlastnosti | Žádný |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[Shora dolů](cpp-event-data-types/top-down.md) |
|  | Popis | Vyskytuje se na začátku a zastavení průchodu celé analýzy programu shora dolů. |
| <a name="whole-program-analysis"></a>WHOLE_PROGRAM_ANALYSIS | Typ | Aktivita |
|  | Nadřazené prvky | [C2_DLL](#c2-dll) |
|  | Podřízené prvky | [BOTTOM_UP](#bottom-up)<br/>[TOP_DOWN](#top-down) |
|  | Vlastnosti | Žádný |
|  | Zachytávání tříd | [Činnosti](cpp-event-data-types/activity.md)<br/>[Analýza wholeprogram](cpp-event-data-types/whole-program-analysis.md) |
|  | Popis | Vyvolá se při spuštění a zastavení fáze analýzy celého programu generování kódu v době propojení. |

::: moniker-end
