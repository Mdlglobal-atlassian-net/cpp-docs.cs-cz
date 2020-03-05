---
title: 'C++Build Insights SDK: tabulka událostí'
description: Odkaz na událost pro sadu Visual C++ Studio Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Events
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2ccc8a4ef707942963b85edc6db9e21e05610b54
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332955"
---
# <a name="c-build-insights-sdk-event-table"></a>C++Build Insights SDK: tabulka událostí

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

## <a name="compiler-events"></a>Události kompilátoru

\ [kompilátoru](#compiler)
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

## <a name="compiler-back-end-events"></a>Back-endové události kompilátoru

[C2_DLL](#c2-dll)\
[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis)\
[TOP_DOWN](#top-down)\
[BOTTOM_UP](#bottom-up)\
[CODE_GENERATION](#code-generation)\
\ [vlákna](#thread)
\ [funkce](#function)
[FORCE_INLINEE](#force-inlinee)

## <a name="linker-events"></a>Události linkeru

\ [linkeru](#linker)
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)\
[EXP_OUTPUT](#exp-output)\
[IMP_LIB_OUTPUT](#imp-lib-output)\
[LIB_OUTPUT](#lib-output)\
[PASS1](#pass1)\
[PRE_LTCG_OPT_REF](#pre-ltcg-opt-ref)\
[LTCG](#ltcg)\
[OPT_REF](#opt-ref)\
[OPT_ICF](#opt-icf)\
[OPT_LBR](#opt-lbr)\
[PASS2](#pass2)

## <a name="event-table"></a>Tabulka událostí

| Událost | Vlastnost | Popis |
|--|--|--|
| <a name="back-end-pass"></a>BACK_END_PASS | Typ | Aktivita |
|  | Nadřazený | [PŘEPÍNAČ](#compiler) |
|  | Elementy | [C2_DLL](#c2-dll) |
|  | Vlastnosti | -Absolutní cesta k vstupnímu zdrojovému souboru<br/>-Absolutní cesta k souboru výstupního objektu |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[BackEndPass](cpp-event-data-types/back-end-pass.md) |
|  | Popis | Nastane na začátku a zastavení back-endu kompilátoru. Tento průchod zodpovídá za účelem optimalizace analyzovanéhoC++ zdrojového kódu jazyka C a jeho převodu do strojového kódu. |
| <a name="bottom-up"></a>BOTTOM_UP | Typ | Aktivita |
|  | Nadřazený | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Elementy | Žádná |
|  | Vlastnosti | Žádná |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[BottomUp](cpp-event-data-types/bottom-up.md) |
|  | Popis | Nastane na začátku a na konci úplného průchodu analýzy celého programu. |
| <a name="c1-dll"></a>C1_DLL | Typ | Aktivita |
|  | Nadřazený | [FRONT_END_PASS](#front-end-pass) |
|  | Elementy | [FRONT_END_FILE](#front-end-file)<br/>[SYMBOL_NAME](#symbol-name)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Vlastnosti | Žádná |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[C1DLL](cpp-event-data-types/c1-dll.md) |
|  | Popis | Proběhne na začátku a zastavení volání *C1. dll* nebo *c1xx. dll* . Tyto knihovny DLL jsou C a C++ front-end kompilátoru. Jsou vyvolány výhradně pomocí ovladače kompilátoru (*CL. exe*). |
| <a name="c2-dll"></a>C2_DLL | Typ | Aktivita |
|  | Nadřazený | [BACK_END_PASS](#back-end-pass)<br/>[LTCG](#ltcg) |
|  | Elementy | [CODE_GENERATION](#code-generation)<br/>[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Vlastnosti | Žádná |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[C2DLL](cpp-event-data-types/c2-dll.md) |
|  | Popis | Nastane na začátku a zastavení vyvolání *C2. dll* . Tato knihovna DLL je back-end kompilátoru. Je volána ovladačem kompilátoru (*CL. exe*). Je také vyvolána linkerem (*Link. exe*) při použití generování kódu při propojování. |
| <a name="code-generation"></a>CODE_GENERATION | Typ | Aktivita |
|  | Nadřazený | [C2_DLL](#c2-dll) |
|  | Elementy | [FUNCTION](#function)<br/>[Doporučujeme](#thread) |
|  | Vlastnosti | Žádná |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[Strategii](cpp-event-data-types/code-generation.md) |
|  | Popis | Nastane na začátku a zastavování fáze generování kódu back-endu. |
| <a name="command-line"></a>COMMAND_LINE | Typ | Jednoduchá událost |
|  | Nadřazený | [PŘEPÍNAČ](#compiler)<br/>[LINKERU](#linker) |
|  | Elementy | Žádná |
|  | Vlastnosti | – Příkazový řádek, který se použil k vyvolání souboru *CL. exe* nebo *Link. exe.* |
|  | Třídy zachycení | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Řádek](cpp-event-data-types/command-line.md) |
|  | Popis | Nastane, pokud se kompilátor a linker dokončí vyhodnocování příkazového řádku. Vyhodnocený příkazový řádek obsahuje všechny parametry *CL. exe* a *Link. exe* předané prostřednictvím souboru odpovědí. Obsahuje také parametry nástroje *CL. exe* a *Link. exe* předané pomocí proměnných prostředí, jako je cl, \_CL\_, link a \_Link\_. |
| <a name="compiler"></a>PŘEPÍNAČ | Typ | Aktivita |
|  | Nadřazený | Žádná |
|  | Elementy | [BACK_END_PASS](#back-end-pass)<br/>[COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[FILE_INPUT](#file-input)<br/>[OBJ_OUTPUT](#obj-output)<br/>[FRONT_END_PASS](#front-end-pass) |
|  | Vlastnosti | – Verze kompilátoru<br/>– Pracovní adresář<br/>– Absolutní cesta k vyvolanému *CL. exe* |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[Vyvolání](cpp-event-data-types/invocation.md)<br/>[Přepínač](cpp-event-data-types/compiler.md) |
|  | Popis | Nastane na začátku a zastavování programu *CL. exe* vyvolání. |
| <a name="environment-variable"></a>ENVIRONMENT_VARIABLE | Typ | Jednoduchá událost |
|  | Nadřazený | [PŘEPÍNAČ](#compiler)<br/>[LINKERU](#linker) |
|  | Elementy | Žádná |
|  | Vlastnosti | – Název proměnné prostředí<br/>– Hodnota proměnné prostředí. |
|  | Třídy zachycení | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Objekt EnvironmentVariable](cpp-event-data-types/environment-variable.md) |
|  | Popis | Vyvolá se jednou pro každou existující proměnnou prostředí v době vyvolání souboru *CL. exe* nebo *Link. exe* . |
| <a name="executable-image-output"></a>EXECUTABLE_IMAGE_OUTPUT | Typ | Jednoduchá událost |
|  | Nadřazený | [LINKERU](#linker) |
|  | Elementy | Žádná |
|  | Vlastnosti | – Absolutní cesta ke knihovně DLL nebo spustitelný výstupní soubor. |
|  | Třídy zachycení | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Výstup](cpp-event-data-types/file-output.md)<br/>[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md) |
|  | Popis | Vyvolá se v případě, že jeden ze vstupů linkeru je knihovna DLL nebo spustitelný soubor bitové kopie. |
| <a name="exp-output"></a>EXP_OUTPUT | Typ | Jednoduchá událost |
|  | Nadřazený | [LINKERU](#linker) |
|  | Elementy | Žádná |
|  | Vlastnosti | – Absolutní cesta k výstupnímu souboru *. exp* . |
|  | Třídy zachycení | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Výstup](cpp-event-data-types/file-output.md)<br/>[ExpOutput](cpp-event-data-types/exp-output.md) |
|  | Popis | Vyvolá se v případě, že jeden z výstupů linkeru je soubor *. exp* . |
| <a name="file-input"></a>FILE_INPUT | Typ | Jednoduchá událost |
|  | Nadřazený | [PŘEPÍNAČ](#compiler)<br/>[LINKERU](#linker) |
|  | Elementy | Žádná |
|  | Vlastnosti | – Absolutní cesta ke vstupnímu souboru<br/>– Typ vstupního souboru |
|  | Třídy zachycení | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Vstup vstupu](cpp-event-data-types/file-input.md) |
|  | Popis | Dojde k oznámení vstupu *CL. exe* nebo *Link. exe* . |
| <a name="force-inlinee"></a>FORCE_INLINEE | Typ | Jednoduchá událost |
|  | Nadřazený | [FUNCTION](#function) |
|  | Elementy | Žádná |
|  | Vlastnosti | – Název funkce s vynucenou vloženou funkcí.<br/>– Velikost vynuceně vložené funkce reprezentovaná jako počet zprostředkujících instrukcí. |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[ForceInlinee](cpp-event-data-types/force-inlinee.md) |
|  | Popis | Vyvolá se v případě, že je vynucena funkce – vložená do jiné funkce pomocí klíčového slova `__forceinline`. |
| <a name="front-end-file"></a>FRONT_END_FILE | Typ | Aktivita |
|  | Nadřazený | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file) |
|  | Elementy | [FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Vlastnosti | – Absolutní cesta k souboru. |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[FrontEndFile](cpp-event-data-types/front-end-file.md) |
|  | Popis | Nastane, pokud se spustí front-end kompilátoru a zastaví se zpracování souboru. Tato událost je rekurzivní. Rekurze nastane, pokud front-end analyzuje zahrnuté soubory. |
| <a name="front-end-pass"></a>FRONT_END_PASS | Typ | Aktivita |
|  | Nadřazený | [PŘEPÍNAČ](#compiler) |
|  | Elementy | [C1_DLL](#c1-dll) |
|  | Vlastnosti | -Absolutní cesta k vstupnímu zdrojovému souboru<br/>-Absolutní cesta k souboru výstupního objektu |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[FrontEndPass](cpp-event-data-types/front-end-pass.md) |
|  | Popis | Nastane na začátku a zastavení front-endu kompilátoru. Tento úspěch zodpovídá za analýzu C/C++ zdrojového kódu a jeho převod do mezilehlého jazyka. |
| <a name="function"></a>SLOUŽÍ | Typ | Aktivita |
|  | Nadřazený | [CODE_GENERATION](#code-generation)<br/>[Doporučujeme](#thread)<br/>[TOP_DOWN](#top-down) |
|  | Elementy | [FORCE_INLINEE](#force-inlinee) |
|  | Vlastnosti | – Název funkce |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[Slouží](cpp-event-data-types/function.md) |
|  | Popis | Nastane při spuštění a ukončení generování kódu pro funkci. |
| <a name="imp-lib-output"></a>IMP_LIB_OUTPUT | Typ | Jednoduchá událost |
|  | Nadřazený | [LINKERU](#linker) |
|  | Elementy | Žádná |
|  | Vlastnosti | – Absolutní cesta k výstupnímu souboru knihovny importu. |
|  | Třídy zachycení | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Výstup](cpp-event-data-types/file-output.md)<br/>[ImpLibOutput](cpp-event-data-types/imp-lib-output.md) |
|  | Popis | Nastane, pokud je jeden z výstupů linkeru knihovna importu. |
| <a name="lib-output"></a>LIB_OUTPUT | Typ | Jednoduchá událost |
|  | Nadřazený | [LINKERU](#linker) |
|  | Elementy | Žádná |
|  | Vlastnosti | – Absolutní cesta k výstupnímu souboru statické knihovny. |
|  | Třídy zachycení | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Výstup](cpp-event-data-types/file-output.md)<br/>[LibOutput](cpp-event-data-types/lib-output.md) |
|  | Popis | Nastane, pokud je jeden z výstupů linkeru Statická knihovna. |
| <a name="linker"></a>LINKERU | Typ | Aktivita |
|  | Nadřazený | Žádná |
|  | Elementy | [COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)<br/>[EXP_OUTPUT](#exp-output)<br/>[FILE_INPUT](#file-input)<br/>[IMP_LIB_OUTPUT](#imp-lib-output)<br/>[LIB_OUTPUT](#lib-output)<br/>[PASS1](#pass1)<br/>[PASS2](#pass2) |
|  | Vlastnosti | – Verze linkeru<br/>– Pracovní adresář<br/>– Absolutní cesta k vyvolanému *propojení. exe* |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[Vyvolání](cpp-event-data-types/invocation.md)<br/>[Linker](cpp-event-data-types/linker.md) |
|  | Popis | Nastane na začátku a zastavování volání *Link. exe* . |
| <a name="ltcg"></a>LTCG | Typ | Aktivita |
|  | Nadřazený | [PASS1](#pass1) |
|  | Elementy | [C2_DLL](#c2-dll) |
|  | Vlastnosti | Žádná |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[LTCG](cpp-event-data-types/ltcg.md) |
|  | Popis | Nastane na začátku a zastavování generování kódu při propojování. |
| <a name="obj-output"></a>OBJ_OUTPUT | Typ | Jednoduchá událost |
|  | Nadřazený | [PŘEPÍNAČ](#compiler) |
|  | Elementy | Žádná |
|  | Vlastnosti | – Absolutní cesta k výstupnímu souboru *. obj* |
|  | Třídy zachycení | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Výstup](cpp-event-data-types/file-output.md)<br/>[ObjOutput](cpp-event-data-types/obj-output.md) |
|  | Popis | Nastane jednou pro každý výstup *. obj* vytvořený pomocí *CL. exe*. |
| <a name="opt-icf"></a>OPT_ICF | Typ | Aktivita |
|  | Nadřazený | [PASS1](#pass1) |
|  | Elementy | Žádná |
|  | Vlastnosti | Žádná |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[OptICF](cpp-event-data-types/opt-icf.md) |
|  | Popis | Proběhne na začátku a zastavení identické optimalizace linkeru COMDAT skládání (/OPT: ICF). |
| <a name="opt-lbr"></a>OPT_LBR | Typ | Aktivita |
|  | Nadřazený | [PASS1](#pass1) |
|  | Elementy | Žádná |
|  | Vlastnosti | Žádná |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[OptLBR](cpp-event-data-types/opt-lbr.md) |
|  | Popis | Proběhne na začátku a zastavení optimalizace linkeru dlouhé větve (/OPT: LBR). |
| <a name="opt-ref"></a>OPT_REF | Typ | Aktivita |
|  | Nadřazený | [PASS1](#pass1) |
|  | Elementy | Žádná |
|  | Vlastnosti | Žádná |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[OptRef](cpp-event-data-types/opt-ref.md) |
|  | Popis | Nastane na začátku a zastavování optimalizace linkeru neodkazované funkce a eliminace dat (/OPT: REF). |
| <a name="pass1"></a>PASS1 | Typ | Aktivita |
|  | Nadřazený | [LINKERU](#linker) |
|  | Elementy | [LTCG](#ltcg)<br/>[OPT_ICF](#opt-icf)<br/>[OPT_LBR](#opt-lbr)<br/>[OPT_REF](#opt-ref) |
|  | Vlastnosti | Žádná |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[Pass1](cpp-event-data-types/pass1.md) |
|  | Popis | Nastane na začátku a zastavení průchodu linkeru 1. |
| <a name="pass2"></a>PASS2 | Typ | Aktivita |
|  | Nadřazený | [LINKERU](#linker) |
|  | Elementy | Žádná |
|  | Vlastnosti | Žádná |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[Pass2](cpp-event-data-types/pass2.md) |
|  | Popis | Nastane na začátku a zastavení Pass linkeru 2. |
| <a name="pre-ltcg-opt-ref"></a>PRE_LTCG_OPT_REF | Typ | Aktivita |
|  | Nadřazený | [PASS1](#pass1) |
|  | Elementy | Žádná |
|  | Vlastnosti | Žádná |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md) |
|  | Popis | Nastane na začátku a zastavení průchodu optimalizace linkeru, které eliminují neodkazované funkce a data (/OPT: REF). Provede se před tím, než se vygenerování kódu při propojování. |
| <a name="symbol-name"></a>SYMBOL_NAME | Typ | Jednoduchá událost |
|  | Nadřazený | [C1_DLL](#c1-dll) |
|  | Elementy | Žádná |
|  | Vlastnosti | -Klíč typu<br/> – Název typu |
|  | Třídy zachycení | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Symbol označení](cpp-event-data-types/symbol-name.md) |
|  | Popis | Nastane na konci front-endu průchodu: jednou pro každý typ, který je součástí vytváření instancí šablon. Klíč je číselný identifikátor typu, zatímco název je jeho reprezentace textu. Klíče typů jsou jedinečné v rámci analyzovaného trasování. Nicméně různé klíče přicházející z různých front-end průchodů kompilátoru mohou ukazovat na stejný typ. Porovnávání typů mezi různými průchody front-end kompilátoru vyžaduje použití jejich názvů. Události SYMBOL_NAME jsou generovány na konci front-endu kompilátoru, poté, co byly provedeny všechny instance šablon. |
| <a name="template-instantiation"></a>TEMPLATE_INSTANTIATION | Typ | Aktivita |
|  | Nadřazený | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Elementy | [TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Vlastnosti | – Klíč pro specializovaný typ<br/>– Klíč pro typ primární šablony<br/>– Druh šablony, na kterou se vytvořila instance |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[TemplateInstantiation](cpp-event-data-types/template-instantiation.md) |
|  | Popis | Nastane na začátku a konci vytváření instancí šablony. Vytvoří se instance typu primární šablony (například `vector`), což vede k vytvoření specializovaného typu (například `std::vector<int>`). Klíč je uveden pro oba typy. Použijte událost [SYMBOL_NAME](#symbol-name) k převedení klíče na název typu. Klíče typů jsou jedinečné v rámci analyzovaného trasování. Nicméně různé klíče přicházející z různých front-end průchodů kompilátoru mohou ukazovat na stejný typ. Porovnávání typů mezi různými průchody front-end kompilátoru vyžaduje použití názvů symbolů. Tato událost je rekurzivní. Rekurze nastane v některých případech, pokud je front-end instancí vnořených šablon. |
| <a name="thread"></a>Doporučujeme | Typ | Aktivita |
|  | Nadřazený | [CODE_GENERATION](#code-generation)<br/>[TOP_DOWN](#top-down) |
|  | Elementy | [FUNCTION](#function) |
|  | Vlastnosti | Žádná |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[Doporučujeme](cpp-event-data-types/thread.md) |
|  | Popis | Nastane na začátku a konci spuštění vlákna back-endu kompilátoru. Pozastavené vlákno je považováno za ukončené. Probuzený vlákno se považuje za zahájené. |
| <a name="top-down"></a>TOP_DOWN | Typ | Aktivita |
|  | Nadřazený | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Elementy | [FUNCTION](#function)<br/>[Doporučujeme](#thread) |
|  | Vlastnosti | Žádná |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[TopDown](cpp-event-data-types/top-down.md) |
|  | Popis | Vyvolá se na začátku a zastavení úplného horního průchodu analýzy celého programu. |
| <a name="whole-program-analysis"></a>WHOLE_PROGRAM_ANALYSIS | Typ | Aktivita |
|  | Nadřazený | [C2_DLL](#c2-dll) |
|  | Elementy | [BOTTOM_UP](#bottom-up)<br/>[TOP_DOWN](#top-down) |
|  | Vlastnosti | Žádná |
|  | Třídy zachycení | [Aktivita](cpp-event-data-types/activity.md)<br/>[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) |
|  | Popis | Nastane na začátku a zastavení fáze analýzy celého programu při generování kódu při propojování. |

::: moniker-end
