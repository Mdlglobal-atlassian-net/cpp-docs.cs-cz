---
title: C++Sada SDK pro Build Insights
description: Přehled sady Visual Studio C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyzing
- Relogging
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5aafcc65bc30de77131d1945c9f4e78361db14ed
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332395"
---
# <a name="c-build-insights-sdk"></a>C++Sada SDK pro Build Insights

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Sada C++ SDK pro Build Insights je kolekce rozhraní API, která umožňují vytvářet přizpůsobené nástroje nad platformou pro C++ vytváření sestav. Tato stránka poskytuje přehled vysoké úrovně, které vám pomůžou začít.

## <a name="obtaining-the-sdk"></a>Získání sady SDK

Sadu SDK pro C++ Build Insights můžete stáhnout jako balíček NuGet pomocí následujících kroků:

1. V aplikaci Visual Studio 2017 nebo novější vytvořte nový C++ projekt.
1. V podokně **Průzkumník řešení** klikněte pravým tlačítkem myši na projekt.
1. V místní nabídce vyberte **Spravovat balíčky NuGet** .
1. V pravém horním rohu vyberte zdroj balíčku **NuGet.org** .
1. Vyhledejte nejnovější verzi balíčku Microsoft. cpp. BuildInsights.
1. Klikněte na tlačítko **nainstalovat**.
1. Přijměte licenci.

Přečtěte si informace o obecných konceptech obklopujících sadu SDK. Můžete také získat přístup k oficiálnímu [ C++ úložišti GitHub ukázek Build Insights](https://github.com/microsoft/cpp-build-insights-samples) , abyste viděli příklady C++ reálných aplikací, které používají sadu SDK.

## <a name="collecting-a-trace"></a>Shromažďování trasování

Použití sady C++ SDK pro Build Insights k analýze událostí z MSVC sada nástrojů vyžaduje, abyste nejdřív shromáždili trasování. Sada SDK využívá trasování událostí pro Windows (ETW) jako základní trasovací technologii. Shromažďování trasování lze provádět dvěma způsoby:

### <a name="method-1-using-vcperf-in-visual-studio-2019-and-above"></a>Metoda 1: použití vcperf v aplikaci Visual Studio 2019 a vyšší

1. Otevřete x64 Native Tools Command Prompt se zvýšenými oprávněními pro VS 2019.
1. Spusťte následující příkaz: `vcperf /start MySessionName`
1. Sestavte projekt.
1. Spusťte následující příkaz: `vcperf /stopnoanalyze MySessionName outputTraceFile.etl`

   > [!IMPORTANT]
   > Při zastavování trasování pomocí vcperf použijte příkaz `/stopnoanalyze`. Nemůžete použít C++ sadu SDK pro Build Insights k analýze trasování zastavených běžným `/stop`m příkazem.

### <a name="method-2-programmatically"></a>Metoda 2: programově

Pomocí kterékoli z těchto C++ funkcí kolekce Trace Insights SDK pro buildy můžete spouštět a zastavovat trasování prostřednictvím kódu programu. **Program, který spouští Tato volání funkce, musí mít oprávnění správce.** Pouze funkce spuštění a zastavení trasování vyžadují oprávnění správce. Všechny ostatní funkce v sadě C++ Build Insights SDK je možné provést bez nich.

### <a name="sdk-functions-related-to-trace-collection"></a>Funkce sady SDK související se shromažďováním trasování

| Funkce | Rozhraní API C++ | C API |
|--|--|--|
| Spuštění trasování | [StartTracingSession](functions/start-tracing-session.md) | [StartTracingSessionA](functions/start-tracing-session-a.md)<br />[StartTracingSessionW](functions/start-tracing-session-w.md) |
| Zastavení trasování | [StopTracingSession](functions/stop-tracing-session.md) | [StopTracingSessionA](functions/stop-tracing-session-a.md)<br />[StopTracingSessionW](functions/stop-tracing-session-w.md) |
| Zastavení trasování a<br />Okamžitá analýza výsledku | [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md) | [StopAndAnalyzeTracingSessionA](functions/stop-and-analyze-tracing-session-a.md)<br />[StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session-w.md) |
| Zastavení trasování a<br />okamžité znovu protokolování výsledku | [StopAndRelogTracingSession](functions/stop-and-relog-tracing-session.md) | [StopAndRelogTracingSessionA](functions/stop-and-relog-tracing-session-a.md)<br />[StopAndRelogTracingSessionW](functions/stop-and-relog-tracing-session-w.md) |

Níže uvedené části ukazují, jak nakonfigurovat analýzu nebo znovu vytvořit relaci. Vyžaduje se pro kombinované funkce, jako je [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md).

## <a name="consuming-a-trace"></a>Spotřebovávání trasování

Jakmile budete mít trasování ETW, rozbalte ho pomocí C++ sady SDK pro Build Insights. Sada SDK poskytuje události ve formátu, který umožňuje rychlé vývoj nástrojů. Nedoporučujeme využívat nezpracované trasování ETW bez použití sady SDK. Formát události, který používá MSVC, je nedokumentované, optimalizované pro škálování na obrovský buildy a obtížné vydávat smysl. Rozhraní API pro C++ Build Insights SDK je navíc stabilní, ale nezpracovaný formát trasování ETW se může změnit bez předchozího upozornění.

### <a name="sdk-types-and-functions-related-to-trace-consumption"></a>Typy a funkce sady SDK související se spotřebou trasování

| Funkce | Rozhraní API C++ | C API | Poznámky: |
|--|--|--|--|
| Nastavení zpětných volání událostí | [IAnalyzer](other-types/ianalyzer-class.md)<br />[IRelogger](other-types/irelogger-class.md) | [ANALYSIS_CALLBACKS](other-types/analysis-callbacks-struct.md)<br />[RELOG_CALLBACKS](other-types/relog-callbacks-struct.md) | Sada C++ SDK pro Build Insights poskytuje události prostřednictvím funkcí zpětného volání. V C++nástroji implementujte funkce zpětného volání vytvořením třídy analyzátoru nebo reprotokolovacího nástroje, která dědí rozhraní IAnalyzer nebo IRelogger. V jazyce C implementujte zpětná volání v globálních funkcích a poskytněte ukazatelům na ně ve ANALYSIS_CALLBACKS nebo RELOG_CALLBACKS struktuře. |
| Vytváření skupin | [MakeStaticAnalyzerGroup](functions/make-static-analyzer-group.md)<br />[MakeStaticReloggerGroup](functions/make-static-relogger-group.md)<br />[MakeDynamicAnalyzerGroup](functions/make-dynamic-analyzer-group.md)<br />[MakeDynamicReloggerGroup](functions/make-dynamic-relogger-group.md) |  | C++ Rozhraní API poskytuje pomocné funkce a typy pro seskupení více objektů analyzátoru a přeprotokolovacího nástroje. Skupiny představují úhledný způsob, jak rozdělit složitou analýzu do jednodušších kroků. [vcperf](https://github.com/microsoft/vcperf) je uspořádán tímto způsobem. |
| Analýza nebo přehlašování | [Analýza](functions/analyze.md)<br />[Relog](functions/relog.md) | [Analyzovat](functions/analyze-a.md)<br />[AnalyzeW](functions/analyze-w.md)<br />[Relog](functions/relog-a.md)<br />[RelogW](functions/relog-w.md) |  |

### <a name="analyzing-and-relogging"></a>Analýza a znovu protokolování

Spotřebovávání trasování se provádí prostřednictvím relace analýzy nebo relace znovu protokolovaných protokolů.

Použití běžné analýzy je vhodné pro většinu scénářů. Tato metoda poskytuje flexibilitu pro výběr formátu výstupu: `printf` text, XML, JSON, databáze, volání REST atd.

Opětovné protokolování slouží k analýzám zvláštního účelu, které potřebují k vytváření výstupního souboru ETW. Pomocí funkce opětovného protokolování můžete události sestavení C++ s přehledy přeložit do vlastního formátu událostí ETW. Vhodným použitím C++ opětovného protokolování by bylo připojení dat Build Insights k existujícím nástrojům a infrastruktuře ETW. [Vcperf](https://github.com/microsoft/vcperf) například využívá rozhraní pro přeprotokolování. To je proto, že musí vyrozumět datům, které může nástroj Windows Performance Analyzer a nástroj ETW pochopit. Některé předchozí znalosti o tom, jak funguje ETW, se vyžadují v případě, že plánujete používat rozhraní pro přeprotokolování.

### <a name="creating-analyzer-groups"></a>Vytváření skupin analyzátorů

Je důležité, abyste věděli, jak vytvořit skupiny. Tady je příklad, který ukazuje, jak vytvořit skupinu analyzátorů, která tiskne *Hello, World!* pro každou událost zahájení aktivity, kterou obdrží.

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

## <a name="using-events"></a>Používání událostí

### <a name="sdk-types-and-functions-related-to-events"></a>Typy a funkce sady SDK související s událostmi

| Funkce | Rozhraní API C++ | C API | Poznámky: |
|--|--|--|--|
| Události porovnání a filtrování | [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md)<br />[MatchEventStack](functions/match-event-stack.md)<br />[MatchEventInMemberFunction](functions/match-event-in-member-function.md)<br />[MatchEvent](functions/match-event.md) |  | C++ Rozhraní API nabízí funkce, které usnadňují extrakci událostí, které vás zajímají z vašich trasování. V rozhraní API jazyka C musí být toto filtrování provedeno rukou. |
| Datové typy událostí | [Aktivita](cpp-event-data-types/activity.md)<br />[BackEndPass](cpp-event-data-types/back-end-pass.md)<br />[BottomUp](cpp-event-data-types/bottom-up.md)<br />[C1DLL](cpp-event-data-types/c1-dll.md)<br />[C2DLL](cpp-event-data-types/c2-dll.md)<br />[Strategii](cpp-event-data-types/code-generation.md)<br />[Řádek](cpp-event-data-types/command-line.md)<br />[Přepínač](cpp-event-data-types/compiler.md)<br />[CompilerPass](cpp-event-data-types/compiler-pass.md)<br />[Objekt EnvironmentVariable](cpp-event-data-types/environment-variable.md)<br />[Události](cpp-event-data-types/event.md)<br />[Skupiny událostí](cpp-event-data-types/event-group.md)<br />[EventStack](cpp-event-data-types/event-stack.md)<br />[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md)<br />[ExpOutput](cpp-event-data-types/exp-output.md)<br />[Vstup vstupu](cpp-event-data-types/file-input.md)<br />[Výstup](cpp-event-data-types/file-output.md)<br />[ForceInlinee](cpp-event-data-types/force-inlinee.md)<br />[FrontEndFile](cpp-event-data-types/front-end-file.md)<br />[FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md)<br />[FrontEndPass](cpp-event-data-types/front-end-pass.md)<br />[Slouží](cpp-event-data-types/function.md)<br />[ImpLibOutput](cpp-event-data-types/imp-lib-output.md)<br />[Vyvolání](cpp-event-data-types/invocation.md)<br />[Nevolání](cpp-event-data-types/invocation-group.md)<br />[LibOutput](cpp-event-data-types/lib-output.md)<br />[Linker](cpp-event-data-types/linker.md)<br />[Propojovacího programu](cpp-event-data-types/linker-group.md)<br />[LinkerPass](cpp-event-data-types/linker-pass.md)<br />[LTCG](cpp-event-data-types/ltcg.md)<br />[ObjOutput](cpp-event-data-types/obj-output.md)<br />[OptICF](cpp-event-data-types/opt-icf.md)<br />[OptLBR](cpp-event-data-types/opt-lbr.md)<br />[OptRef](cpp-event-data-types/opt-ref.md)<br />[Pass1](cpp-event-data-types/pass1.md)<br />[Pass2](cpp-event-data-types/pass2.md)<br />[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md)<br />[SimpleEvent](cpp-event-data-types/simple-event.md)<br />[Symbol označení](cpp-event-data-types/symbol-name.md)<br />[TemplateInstantiation](cpp-event-data-types/template-instantiation.md)<br />[TemplateInstantiationGroup](cpp-event-data-types/template-instantiation-group.md)<br />[Doporučujeme](cpp-event-data-types/thread.md)<br />[TopDown](cpp-event-data-types/top-down.md)<br />[TraceInfo](cpp-event-data-types/trace-info.md)<br />[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) | [CL_PASS_DATA](c-event-data-types/cl-pass-data-struct.md)<br />[EVENT_COLLECTION_DATA](c-event-data-types/event-collection-data-struct.md)<br />[EVENT_DATA](c-event-data-types/event-data-struct.md)<br />[EVENT_ID](c-event-data-types/event-id-enum.md)<br />[FILE_DATA](c-event-data-types/file-data-struct.md)<br />[FILE_TYPE_CODE](c-event-data-types/file-type-code-enum.md)<br />[FRONT_END_FILE_DATA](c-event-data-types/front-end-file-data-struct.md)<br />[FUNCTION_DATA](c-event-data-types/function-data-struct.md)<br />[FUNCTION_FORCE_INLINEE_DATA](c-event-data-types/function-force-inlinee-data-struct.md)<br />[INVOCATION_DATA](c-event-data-types/invocation-data-struct.md)<br />[INVOCATION_VERSION_DATA](c-event-data-types/invocation-version-data-struct.md)<br />[MSVC_TOOL_CODE](c-event-data-types/msvc-tool-code-enum.md)<br />[NAME_VALUE_PAIR_DATA](c-event-data-types/name-value-pair-data-struct.md)<br />[SYMBOL_NAME_DATA](c-event-data-types/symbol-name-data-struct.md)<br />[TEMPLATE_INSTANTIATION_DATA](c-event-data-types/template-instantiation-data-struct.md)<br />[TEMPLATE_INSTANTIATION_KIND_CODE](c-event-data-types/template-instantiation-kind-code-enum.md)<br />[TRACE_INFO_DATA](c-event-data-types/trace-info-data-struct.md)<br />[TRANSLATION_UNIT_PASS_CODE](c-event-data-types/translation-unit-pass-code-enum.md) |  |

### <a name="activities-and-simple-events"></a>Aktivity a jednoduché události

Události přicházejí ve dvou kategoriích: *aktivity* a *jednoduché události*. Aktivity jsou probíhající procesy v čase, které mají začátek a konec. Jednoduché události jsou punctual výskyty a nemají dobu trvání. Při analýze trasování MSVC pomocí sady C++ SDK pro Build Insights obdržíte samostatné události při spuštění a zastavení aktivity. Při výskytu jednoduché události se zobrazí jenom jedna událost.

### <a name="parent-child-relationships"></a>Vztahy nadřazenosti a podřízenosti

Aktivity a jednoduché události spolu vzájemně souvisí prostřednictvím vztahů nadřazenosti a podřízenosti. Nadřazená aktivita aktivity nebo jednoduchá událost je zahrnutá aktivita zahrnující aktivity, ve kterých k nim dochází. Například při kompilování zdrojového souboru kompilátor musí soubor analyzovat a pak vytvořit kód. Aktivity analýzy a generování kódu jsou podřízenými položkami aktivity kompilátoru.

Jednoduché události nemají dobu trvání, takže se v nich nic jiného nemůžete stát. V takovém případě nikdy nemají žádné podřízené položky.

Relace nadřazený-podřízený každé aktivity a jednoduchá událost jsou uvedeny v [tabulce událostí](event-table.md). Pochopení těchto vztahů je důležité při využívání C++ událostí s přehledem sestavení. Často je budete muset spoléhat na to, abyste pochopili úplný kontext události.

### <a name="properties"></a>Vlastnosti

Všechny události mají následující vlastnosti:

| Vlastnost | Popis |
|--|--|
| Identifikátor typu | Číslo, které jedinečně identifikuje typ události. |
| Identifikátor instance | Číslo, které jedinečně identifikuje událost v rámci trasování. V případě, že se v trasování vyskytují dvě události stejného typu, získá jedinečný identifikátor instance. |
| Čas spuštění | Čas spuštění aktivity nebo čas, kdy došlo k jednoduché události. |
| Identifikátor procesu | Číslo určující proces, ve kterém došlo k události. |
| Identifikátor vlákna | Číslo určující vlákno, ve kterém došlo k události. |
| Index procesoru | Index založený na nule, který označuje, který logický procesor vyvolal událost. |
| Název události | Řetězec, který popisuje typ události. |

Všechny aktivity kromě jednoduchých událostí mají také tyto vlastnosti:

| Vlastnost | Popis |
|--|--|
| Čas zastavení | Čas, kdy se aktivita zastavila |
| Exkluzivní doba trvání | Čas strávený aktivitou s výjimkou času stráveného v jeho podřízených činnostech. |
| Čas procesoru | Čas, kdy CPU strávilo provádění kódu ve vlákně připojeném k aktivitě. Nezahrnuje čas, kdy bylo vlákno připojené k aktivitě v režimu spánku. |
| Exkluzivní čas procesoru | Stejné jako u času procesoru, ale s výjimkou času procesoru stráveného podřízenými aktivitami. |
| Zodpovědnost za pracovní dobu na Wall hodiny | Příspěvek aktivity k celkovému času na zeď. Časová prodleva při chodu zohledňuje paralelismus mezi aktivitami. Řekněme například, že se dva nesouvisející aktivity spouštějí paralelně. Obě mají dobu 10 sekund a přesně stejný čas spuštění a zastavení. V tomto případě sestavuje Build Insights zodpovědnost po dobu 5 sekund. Naproti tomu platí, že pokud tyto aktivity spustí jednu po druhé bez překrytí, jim se jim přiřadí časová zodpovědnost za 10 sekund. |
| Exkluzivní časová zodpovědnost na zeď | Stejné jako v případě časových zodpovědností na zdi, ale vyloučí zodpovědnost za pracovní dobu v rámci podřízených aktivit. |

Některé události mají své vlastnosti nad rámec těch, které jsou uvedeny. V tomto případě jsou tyto další vlastnosti uvedeny v [tabulce událostí](event-table.md).

### <a name="consuming-events-provided-by-the-c-build-insights-sdk"></a>Využívání událostí poskytovaných sadou C++ SDK pro Build Insights

#### <a name="the-event-stack"></a>Zásobník událostí

Pokaždé C++ , když sada SDK pro Build Insights poskytuje událost, je součástí formy zásobníku. Poslední položkou v zásobníku je aktuální událost a položky před jejich nadřazenou hierarchií. Například [LTCG](event-table.md#ltcg) spustit a zastavit události nastávají během průchodu 1 linkeru. V takovém případě zásobník, který jste obdrželi, obsahuje: \[[linkeru](event-table.md#linker), [PASS1](event-table.md#pass1), LTCG\]. Nadřazená hierarchie je užitečná, protože můžete vrátit událost zpět do své kořenové složky. Pokud je výše uvedená aktivita LTCG pomalé, můžete okamžitě zjistit, které volání linkeru bylo zapojeno.

#### <a name="matching-events-and-event-stacks"></a>Vyhovující události a zásobníky událostí

Sada C++ SDK pro Build Insights poskytuje každou událost v trasování, ale většinu času jenom o jejich podmnožině. V některých případech se můžete zajímat jenom o podmnožinu *zásobníků událostí*. Sada SDK poskytuje zařízení, která vám pomůžou rychle extrahovat události nebo zásobníky událostí, které potřebujete, a odmítnout ty, které neuděláte. Provedete je pomocí těchto vyhovujících funkcí:

|  |  |
|--|--|
| [MatchEvent](functions/match-event.md) | Ponechejte událost, pokud se shoduje s některým z určených typů. Předají odpovídající události do výrazu lambda nebo jiného typu, který lze volat. Tato funkce nebere v úvahu nadřazenou hierarchii události. |
| [MatchEventInMemberFunction](functions/match-event-in-member-function.md) | Ponechá událost, pokud odpovídá typu zadanému v parametru členské funkce. Předají odpovídající události do členské funkce. Tato funkce nebere v úvahu nadřazenou hierarchii události. |
| [MatchEventStack](functions/match-event-stack.md) | Pokud událost i nadřazená hierarchie odpovídají zadaným typům, ponechejte událost. Předejte událost a odpovídající události nadřazené hierarchie do výrazu lambda nebo jiného typu, který lze volat. |
| [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md) | Pokud událost i jeho nadřazená hierarchie odpovídají typům uvedeným v seznamu parametrů členské funkce, ponechejte událost. Předejte událost a odpovídající události nadřazené hierarchie do členské funkce. |

Zásobník událostí, který odpovídá funkcím, jako `MatchEventStack` povoluje mezery při popisu nadřazené hierarchie, která se má shodovat. Řekněme například, že vás zajímá \[[LINKER](event-table.md#linker) [LTCG](event-table.md#ltcg)\] Stack. By se taky shodovala s \[LINKERu, [PASS1](event-table.md#pass1), LTCG\] Stack. Poslední zadaný typ musí být typ události, který se má shodovat, a není součástí nadřazené hierarchie.

#### <a name="capture-classes"></a>Třídy zachycení

Použití funkcí `Match*` vyžaduje, abyste určili typy, které mají být shodné. Tyto typy jsou vybrány ze seznamu *tříd zachycení*. Třídy zachycení jsou dodávány v několika kategoriích, které jsou popsány níže.

| Kategorie | Popis |
|--|--|
| Přesné | Tyto třídy zachycení se používají ke spárování konkrétního typu události a žádné jiné. Příkladem je třída [kompilátoru](cpp-event-data-types/compiler.md) , která odpovídá události [kompilátoru](event-table.md#compiler) . |
| Použity | Tyto třídy zachycení lze použít k vyhledání libovolné události ze seznamu událostí, které podporují. Například zástupný znak [aktivity](cpp-event-data-types/activity.md) odpovídá jakékoli události aktivity. Dalším příkladem je zástupný znak [CompilerPass](cpp-event-data-types/compiler-pass.md) , který může odpovídat buď [FRONT_END_PASS](event-table.md#front-end-pass) , nebo události [BACK_END_PASS](event-table.md#back-end-pass) . |
| Skupina | Názvy tříd zachycení skupin končí ve *skupině*. Používají se k tomu, aby odpovídaly více událostem stejného typu na řádku a ignorují mezery. Dávají smysl pouze v případě, že odpovídají rekurzivním událostem, protože nevíte, kolik v zásobníku událostí existuje. Například aktivita [FRONT_END_FILE](event-table.md#front-end-file) probíhá pokaždé, když kompilátor analyzuje soubor. Tato aktivita je rekurzivní, protože kompilátor může najít direktivu include při analýze souboru. Třída [FrontEndFile](cpp-event-data-types/front-end-file.md) odpovídá pouze jedné události FRONT_END_FILE v zásobníku. Použijte třídu [FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md) , která odpovídá celé vložené hierarchii. |
| Skupina zástupných znaků | Skupina zástupných znaků kombinuje vlastnosti zástupných znaků a skupin. Jediná třída této kategorie je skupina [volání](cpp-event-data-types/invocation-group.md), která odpovídá a zachytává všechny události [linkeru](event-table.md#linker) a [kompilátoru](event-table.md#compiler) v jednom zásobníku událostí. |

Podívejte se na [tabulku událostí](event-table.md) a zjistěte, které třídy zachycení se dají použít ke spárování jednotlivých událostí.

#### <a name="after-matching-using-captured-events"></a>Po shodě: používá zachycené události.

Po úspěšném dokončení porovnávání `Match*` funkce vytvoří objekty třídy Capture a předají je do zadané funkce. Použijte tyto objekty třídy Capture pro přístup k vlastnostem události.

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
