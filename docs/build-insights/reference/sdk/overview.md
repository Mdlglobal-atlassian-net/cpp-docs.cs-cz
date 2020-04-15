---
title: C++ Přehledy sestavení SDK
description: Přehled sady SDK přehledů sestavení sady Visual Studio C++ .
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyzing
- Relogging
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 126abb0d039227eb269500966d46ef0a729763ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323265"
---
# <a name="c-build-insights-sdk"></a>C++ Přehledy sestavení SDK

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Sada C++ Build Insights SDK je kolekce api, která umožňují vytvářet přizpůsobené nástroje nad platformou C++ Build Insights. Tato stránka poskytuje přehled na vysoké úrovni, který vám pomůže začít.

## <a name="obtaining-the-sdk"></a>Získání sady SDK

Sada C++ Build Insights SDK můžete stáhnout jako balíček NuGet následujícím postupem:

1. Z Visual Studia 2017 a vyšší, vytvořte nový projekt C++.
1. V podokně **Průzkumník řešení** klikněte pravým tlačítkem myši na projekt.
1. V místní nabídce vyberte **Spravovat balíčky NuGet.**
1. Vpravo nahoře vyberte zdroj **nuget.org** balíčku.
1. Vyhledejte nejnovější verzi balíčku Microsoft.Cpp.BuildInsights.
1. Zvolte **Instalovat**.
1. Přijměte licenci.

Přečtěte si další informace o obecných konceptech obklopujících sadu SDK. Můžete také přistupovat k oficiálním [ukázek Přehledů sestavení C++ Úložiště GitHub,](https://github.com/microsoft/cpp-build-insights-samples) abyste viděli příklady skutečných aplikací C++, které používají sdk.

## <a name="collecting-a-trace"></a>Shromažďování trasování

Použití sady C++ Build Insights SDK k analýze událostí přicházejících z řetězce nástrojů MSVC vyžaduje, abyste nejprve shromáždili trasování. Sada SDK využívá trasování událostí pro windows (ETW) jako základní technologii trasování. Shromažďování trasování lze provést dvěma způsoby:

### <a name="method-1-using-vcperf-in-visual-studio-2019-and-above"></a>Metoda 1: použití vcperf v Sadě Visual Studio 2019 a vyšší

1. Otevřete příkazový řádek se zvýšenými oprávněními x64 Native Tools pro VS 2019.
1. Spusťte následující příkaz:`vcperf /start MySessionName`
1. Sestavte projekt.
1. Spusťte následující příkaz:`vcperf /stopnoanalyze MySessionName outputTraceFile.etl`

   > [!IMPORTANT]
   > Použijte `/stopnoanalyze` příkaz při zastavení trasování s vcperf. Sdk s přehledy sestavení C++ nelze použít k analýze `/stop` trasování zastavených běžným příkazem.

### <a name="method-2-programmatically"></a>Metoda 2: programově

Pomocí některé z těchto funkcí shromažďování stop sady C++ sestavení sady SDK můžete programově spouštět a zastavovat trasování. **Program, který spouští tato volání funkcí, musí mít oprávnění správce.** Pouze funkce start a stop trasování vyžadují oprávnění správce. Všechny ostatní funkce v c++ sestavení insights SDK lze provést bez nich.

### <a name="sdk-functions-related-to-trace-collection"></a>Funkce sady SDK související s kolekcí trasování

| Funkce | Rozhraní API C++ | C API |
|--|--|--|
| Spuštění trasování | [Relace StartTracingSession](functions/start-tracing-session.md) | [Spuštění TrasováníRelaceA](functions/start-tracing-session-a.md)<br />[StartTracingSessionW](functions/start-tracing-session-w.md) |
| Zastavení trasování | [StopTracingSession](functions/stop-tracing-session.md) | [StopTracingSessionA](functions/stop-tracing-session-a.md)<br />[StopTracingSessionW](functions/stop-tracing-session-w.md) |
| Zastavení trasování a<br />okamžitá analýza výsledku | [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md) | [StopAndAnalyzeTracingSessionA](functions/stop-and-analyze-tracing-session-a.md)<br />[StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session-w.md) |
| Zastavení trasování a<br />okamžité opětovné přihlášení výsledku | [StopAndRelogTracingSession](functions/stop-and-relog-tracing-session.md) | [StopAndRelogTracingSessionA](functions/stop-and-relog-tracing-session-a.md)<br />[StopAndRelogTracingSessionW](functions/stop-and-relog-tracing-session-w.md) |

Následující části ukazují, jak nakonfigurovat analýzu nebo relaci opětovného přihlášení. Je vyžadována pro kombinované funkce funkce, jako je [například StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md).

## <a name="consuming-a-trace"></a>Konzumace trasování

Jakmile budete mít trasování ETW, použijte C++ Sestavení Insights SDK rozbalit. Sada SDK poskytuje události ve formátu, který umožňuje rychlý vývoj nástrojů. Nedoporučujeme konzumovat sledování nezpracovaných ETW bez použití sady SDK. Formát událostí používaný MSVC je nedokumentovaný, optimalizovaný pro škálování na obrovské sestavení a těžko pochopit. Kromě toho c++ sestavení přehledy SDK rozhraní API je stabilní, zatímco nezpracovaný formát trasování ETW se může změnit bez předchozího upozornění.

### <a name="sdk-types-and-functions-related-to-trace-consumption"></a>Typy a funkce sady SDK související se spotřebou trasování

| Funkce | Rozhraní API C++ | C API | Poznámky |
|--|--|--|--|
| Nastavení zpětná volání událostí | [IAnalyzátor](other-types/ianalyzer-class.md)<br />[IRelogger](other-types/irelogger-class.md) | [ANALYSIS_CALLBACKS](other-types/analysis-callbacks-struct.md)<br />[RELOG_CALLBACKS](other-types/relog-callbacks-struct.md) | Sada C++ Build Insights SDK poskytuje události prostřednictvím funkcí zpětného volání. V jazyce C++ implementujte funkce zpětného volání vytvořením analyzátoru nebo třídy reloggeru, která dědí rozhraní IAnalyzer nebo IRelogger. V C implementovat zpětná volání v globální funkce a poskytují ukazatele na ně v ANALYSIS_CALLBACKS nebo RELOG_CALLBACKS struktury. |
| Skupiny budov | [Skupina MakeStaticAnalyzerGroup](functions/make-static-analyzer-group.md)<br />[MakestaticReloggerSkupina](functions/make-static-relogger-group.md)<br />[MakeDynamicAnalyzerGroup](functions/make-dynamic-analyzer-group.md)<br />[MakeDynamicReloggerSkupina](functions/make-dynamic-relogger-group.md) |  | Rozhraní API jazyka C++ poskytuje pomocné funkce a typy pro seskupení více analyzátorů a reloggerobjektů dohromady. Skupiny jsou úhledný způsob, jak rozdělit komplexní analýzu do jednodušších kroků. [vcperf](https://github.com/microsoft/vcperf) je organizována tímto způsobem. |
| Analýza nebo opětovné přihlášení | [Analýza](functions/analyze.md)<br />[Relog](functions/relog.md) | [AnalyzovatA](functions/analyze-a.md)<br />[AnalyzovatW](functions/analyze-w.md)<br />[RelogA](functions/relog-a.md)<br />[RelogW](functions/relog-w.md) |  |

### <a name="analyzing-and-relogging"></a>Analýza a opětovné přihlášení

Spotřebovávat trasování se provádí prostřednictvím relace analýzy nebo relogging relace.

Použití pravidelné analýzy je vhodné pro většinu scénářů. Tato metoda poskytuje flexibilitu zvolit výstupní `printf` formát: text, xml, JSON, databáze, REST volání a tak dále.

Opětovné zaprotokolování je pro speciální analýzy, které potřebují vytvořit výstupní soubor ETW. Pomocí opětovného protokolování můžete přeložit c++ sestavení insights události do vlastního formátu událostí ETW. Vhodné použití opětovného přihlášení by bylo připojit C++ Sestavení přehledy dat na stávající nástroje ETW a infrastruktury. Například [vcperf](https://github.com/microsoft/vcperf) využívá rozhraní pro opětovné přihlášení. Je to proto, že musí produkovat data Windows Performance Analyzer, nástroj ETW, může pochopit. Některé předchozí znalosti o tom, jak ETW funguje, je nutné, pokud máte v plánu na použití relogging rozhraní.

### <a name="creating-analyzer-groups"></a>Vytváření skupin analyzátorů

Je důležité vědět, jak vytvářet skupiny. Zde je příklad, který ukazuje, jak vytvořit skupinu analyzátorů, která vytiskne *Hello, world!* pro každou událost zahájení aktivity, která obdrží.

```cpp
using namespace Microsoft::Cpp::BuildInsights;

class Hello : public IAnalyzer
{
public:
    AnalysisControl OnStartActivity(
        const EventStack& eventStack) override
    {
        std::cout << "Hello, " << std::endl;
        return AnalysisControl::CONTINUE;
    }
};

class World : public IAnalyzer
{
public:
    AnalysisControl OnStartActivity(
        const EventStack& eventStack) override
    {
        std::cout << "world!" << std::endl;
        return AnalysisControl::CONTINUE;
    }
};

int main()
{
    Hello hello;
    World world;

    // Let's make Hello the first analyzer in the group
    // so that it receives events and prints "Hello, "
    // first.
    auto group = MakeStaticAnalyzerGroup(&hello, &world);

    unsigned numberOfAnalysisPasses = 1;

    // Calling this function initiates the analysis and
    // forwards all events from "inputTrace.etl" to my analyzer
    // group.
    Analyze("inputTrace.etl", numberOfAnalysisPasses, group);

    return 0;
}
```

## <a name="using-events"></a>Použití událostí

### <a name="sdk-types-and-functions-related-to-events"></a>Typy a funkce sady SDK související s událostmi

| Funkce | Rozhraní API C++ | C API | Poznámky |
|--|--|--|--|
| Párování a filtrování událostí | [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md)<br />[Stack matchevent](functions/match-event-stack.md)<br />[MatcheventInMemberFunction](functions/match-event-in-member-function.md)<br />[Událost matchevent](functions/match-event.md) |  | Rozhraní API jazyka C++ nabízí funkce, které usnadňují extrahování událostí, na kterých vám záleží, z vašich trasování. S rozhraním C API toto filtrování musí být provedeno ručně. |
| Datové typy událostí | [Činnosti](cpp-event-data-types/activity.md)<br />[Backendpass](cpp-event-data-types/back-end-pass.md)<br />[Dole nahoru](cpp-event-data-types/bottom-up.md)<br />[C1DLL](cpp-event-data-types/c1-dll.md)<br />[C2DLL](cpp-event-data-types/c2-dll.md)<br />[Generování kódu](cpp-event-data-types/code-generation.md)<br />[Commandline](cpp-event-data-types/command-line.md)<br />[Kompilátoru](cpp-event-data-types/compiler.md)<br />[KompilátorPass](cpp-event-data-types/compiler-pass.md)<br />[Proměnná prostředí](cpp-event-data-types/environment-variable.md)<br />[Událost](cpp-event-data-types/event.md)<br />[Skupina událostí](cpp-event-data-types/event-group.md)<br />[Zásobník událostí](cpp-event-data-types/event-stack.md)<br />[Spustitelný výstup ImageOutput](cpp-event-data-types/executable-image-output.md)<br />[ExpOutput](cpp-event-data-types/exp-output.md)<br />[FileInput](cpp-event-data-types/file-input.md)<br />[Výstup souboru](cpp-event-data-types/file-output.md)<br />[SílaInlinee](cpp-event-data-types/force-inlinee.md)<br />[Soubor frontendů](cpp-event-data-types/front-end-file.md)<br />[FrontendFileGroup](cpp-event-data-types/front-end-file-group.md)<br />[Frontendpass](cpp-event-data-types/front-end-pass.md)<br />[Funkce](cpp-event-data-types/function.md)<br />[ImpLibVýstup](cpp-event-data-types/imp-lib-output.md)<br />[Vyvolání](cpp-event-data-types/invocation.md)<br />[Skupina vyvolání](cpp-event-data-types/invocation-group.md)<br />[LibOutput](cpp-event-data-types/lib-output.md)<br />[Linker](cpp-event-data-types/linker.md)<br />[Skupina linkerů](cpp-event-data-types/linker-group.md)<br />[LinkerPass](cpp-event-data-types/linker-pass.md)<br />[LTCG](cpp-event-data-types/ltcg.md)<br />[ObjVýstup](cpp-event-data-types/obj-output.md)<br />[OptiCF](cpp-event-data-types/opt-icf.md)<br />[OptLBR](cpp-event-data-types/opt-lbr.md)<br />[OptRef](cpp-event-data-types/opt-ref.md)<br />[Průchod1](cpp-event-data-types/pass1.md)<br />[Průchod2](cpp-event-data-types/pass2.md)<br />[Program PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md)<br />[SimpleEvent](cpp-event-data-types/simple-event.md)<br />[Název_symbolu](cpp-event-data-types/symbol-name.md)<br />[ŠablonaVytvoření](cpp-event-data-types/template-instantiation.md)<br />[TemplateInstantiationGroup](cpp-event-data-types/template-instantiation-group.md)<br />[Vlákno](cpp-event-data-types/thread.md)<br />[Shora dolů](cpp-event-data-types/top-down.md)<br />[TraceInfo](cpp-event-data-types/trace-info.md)<br />[Analýza wholeprogram](cpp-event-data-types/whole-program-analysis.md) | [CL_PASS_DATA](c-event-data-types/cl-pass-data-struct.md)<br />[EVENT_COLLECTION_DATA](c-event-data-types/event-collection-data-struct.md)<br />[EVENT_DATA](c-event-data-types/event-data-struct.md)<br />[EVENT_ID](c-event-data-types/event-id-enum.md)<br />[FILE_DATA](c-event-data-types/file-data-struct.md)<br />[FILE_TYPE_CODE](c-event-data-types/file-type-code-enum.md)<br />[FRONT_END_FILE_DATA](c-event-data-types/front-end-file-data-struct.md)<br />[FUNCTION_DATA](c-event-data-types/function-data-struct.md)<br />[FUNCTION_FORCE_INLINEE_DATA](c-event-data-types/function-force-inlinee-data-struct.md)<br />[INVOCATION_DATA](c-event-data-types/invocation-data-struct.md)<br />[INVOCATION_VERSION_DATA](c-event-data-types/invocation-version-data-struct.md)<br />[MSVC_TOOL_CODE](c-event-data-types/msvc-tool-code-enum.md)<br />[NAME_VALUE_PAIR_DATA](c-event-data-types/name-value-pair-data-struct.md)<br />[SYMBOL_NAME_DATA](c-event-data-types/symbol-name-data-struct.md)<br />[TEMPLATE_INSTANTIATION_DATA](c-event-data-types/template-instantiation-data-struct.md)<br />[TEMPLATE_INSTANTIATION_KIND_CODE](c-event-data-types/template-instantiation-kind-code-enum.md)<br />[TRACE_INFO_DATA](c-event-data-types/trace-info-data-struct.md)<br />[TRANSLATION_UNIT_PASS_CODE](c-event-data-types/translation-unit-pass-code-enum.md) |  |

### <a name="activities-and-simple-events"></a>Aktivity a jednoduché akce

Akce se konají ve dvou kategoriích: *aktivity* a *jednoduché akce*. Aktivity jsou probíhající procesy v čase, které mají začátek a konec. Jednoduché události jsou přesné výskyty a nemají dobu trvání. Při analýze trasování MSVC pomocí sady C++ Build Insights SDK obdržíte samostatné události při spuštění a zastavení aktivity. Pokud dojde k jednoduché události, obdržíte pouze jednu událost.

### <a name="parent-child-relationships"></a>Vztahy mezi nadřazeným dítětem

Aktivity a jednoduché události spolu vzájemně souvisejí prostřednictvím vztahů mezi nadřazeným a podřízeným. Nadřazený aktivity nebo jednoduché události je zahrnující aktivity, ve kterém dochází. Například při kompilaci zdrojového souboru kompilátor má analyzovat soubor, pak generovat kód. Analýzy a generování kódu aktivity jsou obě podřízené aktivity kompilátoru.

Jednoduché události nemají dobu trvání, takže se v nich nemůže stát nic jiného. Jako takový, nikdy nemají žádné děti.

Relace nadřazený podřízený jednotlivých aktivit a jednoduché události jsou uvedeny v [tabulce událostí](event-table.md). Znalost těchto vztahů je důležité při využívání c++ build insights události. Často se na ně budete muset spolehnout, abyste pochopili celý kontext události.

### <a name="properties"></a>Vlastnosti

Všechny události mají následující vlastnosti:

| Vlastnost | Popis |
|--|--|
| Identifikátor typu | Číslo, které jednoznačně identifikuje typ události. |
| Identifikátor instance | Číslo, které jednoznačně identifikuje událost v rámci trasování. Pokud dvě události stejného typu dojít v trasování, oba získat jedinečný identifikátor instance. |
| Čas spuštění | Čas zahájení aktivity nebo čas, kdy došlo k jednoduché události. |
| Identifikátor procesu | Číslo, které identifikuje proces, ve kterém k události došlo. |
| Identifikátor vlákna | Číslo, které identifikuje vlákno, ve kterém došlo k události. |
| Index procesoru | Nulový index označující, kterým logickým procesorem byla událost vyzařována. |
| Název události | Řetězec, který popisuje typ události. |

Všechny aktivity jiné než jednoduché události mají také tyto vlastnosti:

| Vlastnost | Popis |
|--|--|
| Zastavit čas | Čas, kdy aktivita zastavena. |
| Výhradní doba trvání | Doba strávená v aktivitě, s výjimkou času stráveného v podřízených aktivitách. |
| Čas procesoru | Čas, který procesor strávil provádění kódu ve vlákně připojenék a aktivity. Nezahrnuje čas, kdy vlákno připojené k aktivitě spalo. |
| Exkluzivní čas procesoru | Stejné jako čas procesoru, ale s výjimkou času procesoru stráveného podřízenými aktivitami. |
| Odpovědnost za dobu nástěnných hodin | Příspěvek aktivity k celkovému času nástěnných hodin. Odpovědnost za dobu na nástěnné mši zohledňuje paralelismus mezi činnostmi. Předpokládejme například, že dvě nesouvisející aktivity běží paralelně. Oba mají dobu trvání 10 sekund a přesně stejný čas spuštění a zastavení. V takovém případě Build Insights přiřadí obě odpovědnosti za čas na zdi hodiny 5 sekund. Naproti tomu pokud tyto aktivity běží jeden po druhém bez překrytí, jsou jim přiřazena odpovědnost za čas na zeď 10 sekund. |
| Výhradní odpovědnost za dobu na zdi | Stejné jako odpovědnost za čas na zdi, ale vylučuje odpovědnost za čas na zdi podřízených aktivit. |

Některé události mají své vlastní vlastnosti nad rámec uvedených. V tomto případě jsou tyto další vlastnosti uvedeny v [tabulce událostí](event-table.md).

### <a name="consuming-events-provided-by-the-c-build-insights-sdk"></a>Náročné události poskytované sadou C++ Build Insights SDK

#### <a name="the-event-stack"></a>Zásobník událostí

Vždy, když C++ Build Insights SDK vám událost, přichází ve formě zásobníku. Poslední položkou v zásobníku je aktuální událost a položky před ní jsou nadřazenou hierarchií. Například [LTCG](event-table.md#ltcg) start a stop události dojít během průchodu 1 propojovacího programu. V tomto případě \[zásobník, který obdržíte, obsahuje: [LINKER](event-table.md#linker), [PASS1](event-table.md#pass1), LTCG\]. Nadřazená hierarchie je vhodná, protože můžete trasovat zpět událost do jejího kořenového adresáře. Pokud je výše uvedená aktivita LTCG pomalá, můžete okamžitě zjistit, které vyvolání linkeru se týkalo.

#### <a name="matching-events-and-event-stacks"></a>Párování událostí a zásobníků událostí

Sada C++ Build Insights SDK poskytuje všechny události v trasování, ale většinu času se staráte pouze o podmnožinu z nich. V některých případech se můžete starat pouze o podmnožinu *zásobníků událostí*. Sada SDK poskytuje zařízení, která vám pomohou rychle extrahovat události nebo zásobník událostí, které potřebujete, a odmítnout ty, které nepotřebujete. Je to děláno prostřednictvím těchto odpovídajících funkcí:

|  |  |
|--|--|
| [Událost matchevent](functions/match-event.md) | Zachovat událost, pokud odpovídá jeden ze zadaných typů. Předávat události spárované na lambda nebo jiný volaný typ. Nadřazená hierarchie události není touto funkcí zohledněna. |
| [MatcheventInMemberFunction](functions/match-event-in-member-function.md) | Zachovat událost, pokud odpovídá typu zadanému v parametru členské funkce. Předávání odpovídající události členské funkce. Nadřazená hierarchie události není touto funkcí zohledněna. |
| [Stack matchevent](functions/match-event-stack.md) | Zachovat událost, pokud událost a její nadřazená hierarchie odpovídají zadané typy. Přepošlete události události a události odpovídající nadřazené hierarchie na lambda nebo jiný volaný typ. |
| [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md) | Zachovat událost, pokud událost a její nadřazená hierarchie odpovídají typům zadaným v seznamu parametrů členské funkce. Přepošle událost a události odpovídající nadřazené hierarchie do členské funkce. |

Odpovídající funkce zásobníku `MatchEventStack` událostí, jako je povolit mezery při popisu nadřazené hierarchie tak, aby odpovídaly. Můžete například říci, že vás \[zajímá zásobník [LINKER](event-table.md#linker), [LTCG.](event-table.md#ltcg) \] To by také \[odpovídalo LINKER,\] [PASS1](event-table.md#pass1), LTCG zásobníku. Poslední zadaný typ musí být typ události, který odpovídá, a není součástí nadřazené hierarchie.

#### <a name="capture-classes"></a>Zachytávání tříd

Použití `Match*` funkcí vyžaduje zadání typů, které chcete spárovat. Tyto typy jsou vybrány ze seznamu *tříd zachycení*. Třídy zachycení jsou uvedeny v několika kategoriích, které jsou popsány níže.

| Kategorie | Popis |
|--|--|
| Stejné | Tyto třídy zachycení se používají k přizpůsobení konkrétní typ události a žádný jiný. Příkladem je třída [KOMPILÁtoru,](cpp-event-data-types/compiler.md) která odpovídá události [KOMPILÁTORu.](event-table.md#compiler) |
| Zástupný znak | Tyto třídy zachycení lze použít k odpovídající jakékoli události ze seznamu událostí, které podporují. Například zástupný znak [Aktivita](cpp-event-data-types/activity.md) odpovídá jakékoli události aktivity. Dalším příkladem je zástupný znak [CompilerPass,](cpp-event-data-types/compiler-pass.md) který může odpovídat [události FRONT_END_PASS](event-table.md#front-end-pass) nebo [BACK_END_PASS.](event-table.md#back-end-pass) |
| Skupina | Názvy tříd zachycení skupiny končí ve *skupině*. Používají se k přizpůsobení více událostí stejného typu v řadě a ignorují mezery. Mají smysl pouze při porovnávání rekurzivních událostí, protože nevíte, kolik jich existuje v zásobníku událostí. Například [FRONT_END_FILE](event-table.md#front-end-file) aktivity se stane pokaždé, když kompilátor analyzuje soubor. Tato aktivita je rekurzivní, protože kompilátor může najít include směrnice při analýzě souboru. Třída [FrontEndFile](cpp-event-data-types/front-end-file.md) odpovídá pouze jedné události FRONT_END_FILE v zásobníku. Třídu [FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md) použijte tak, aby odpovídala celé hierarchii zahrnutí. |
| Skupina zástupných symbolů | Skupina zástupných znaků kombinuje vlastnosti zástupných znaků a skupin. Jedinou třídou této kategorie je [InvocationGroup](cpp-event-data-types/invocation-group.md), které odpovídají a zachycují všechny události [LINKER](event-table.md#linker) a [KOMPILÁTOR](event-table.md#compiler) v jednom zásobníku událostí. |

Informace o tom, které třídy zachycení lze použít ke shodě s jednotlivými událostmi, naleznete v [tabulce událostí.](event-table.md)

#### <a name="after-matching-using-captured-events"></a>Po spárování: použití zachycených událostí

Jakmile je shoda úspěšně dokončena, `Match*` funkce vytvoří objekty třídy zachycení a předají je zadané funkci. Pomocí těchto objektů třídy zachycení přístup k vlastnostem události.

#### <a name="example"></a>Příklad

```cpp
AnalysisControl MyAnalyzer::OnStartActivity(const EventStack& eventStack)
{
    // The event types to match are specified in the PrintIncludes function
    // signature.  
    MatchEventStackInMemberFunction(eventStack, this, &MyAnalyzer::PrintIncludes);
}

// We want to capture event stacks where:
// 1. The current event is a FrontEndFile activity.
// 2. The current FrontEndFile activity has at least one parent FrontEndFile activity
//    and possibly many.
void PrintIncludes(FrontEndFileGroup parentIncludes, FrontEndFile currentFile)
{
    // Once we reach this point, the event stack we are interested in has been matched.
    // The current FrontEndFile activity has been captured into 'currentFile', and
    // its entire inclusion hierarchy has been captured in 'parentIncludes'.

    cout << "The current file being parsed is: " << currentFile.Path() << endl;
    cout << "This file was reached through the following inclusions:" << endl;

    for (auto& f : parentIncludes)
    {
        cout << f.Path() << endl;
    }
}
```

::: moniker-end
