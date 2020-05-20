---
title: Novinky v jazyce C++ v sadě Visual Studio
ms.date: 05/19/2020
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
ms.openlocfilehash: 7c36112f5d0f7f0475782eb40e31179e67ac4485
ms.sourcegitcommit: 3f91111c0350c0237fddb82766c290307f20e659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83630491"
---
# <a name="whats-new-for-c-in-visual-studio"></a>Novinky v jazyce C++ v sadě Visual Studio

::: moniker range=">=vs-2019"

Visual Studio 2019 přináší mnoho aktualizací a oprav do prostředí Microsoft C++. Opravili jsme spoustu chyb a problémů v kompilátoru a nástrojích. Mnohé z těchto problémů byly odeslány zákazníky prostřednictvím [nahlášení problému](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019) a [poskytují návrh](https://developercommunity.visualstudio.com/spaces/62/index.html) možností v části **Odeslat názor**. Děkujeme vám, že hlásíte chyby! Další informace o tom, co je nového ve všech verzích sady Visual Studio, najdete v části [novinky v aplikaci Visual studio 2019](/visualstudio/ide/whats-new-visual-studio-2019). Informace o novinkách jazyka C++ v aplikaci Visual Studio 2017 naleznete v tématu [co je nového pro jazyk c++ v aplikaci Visual studio 2017](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017). Informace o tom, co je nového v jazyce C++ v aplikaci Visual Studio 2015 a starších verzích, najdete v tématu [Visual C++ novinky 2003 až 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="c-compiler"></a>kompilátor C++

- Vylepšená podpora pro funkce C++ 17 a opravy oprav a experimentální Podpora funkcí C++ 20, jako jsou moduly a korutiny. Podrobné informace naleznete v tématu [vylepšení shody C++ v aplikaci Visual Studio 2019](cpp-conformance-improvements.md).

- Tato `/std:c++latest` možnost nyní obsahuje funkce c++ 20, které nejsou nutně kompletní, včetně počáteční podpory pro operátor c++ 20 \< => ("prostorové") pro ucelené porovnání.

- Přepínač kompilátoru jazyka C++ `/Gm` je nyní zastaralý. Pokud je explicitně definován, zvažte možnost zakázat `/Gm` přepínač ve skriptech sestavení. Můžete ale také bezpečně ignorovat upozornění na zastaralost pro `/Gm` , protože při použití příkazu "zpracovávat upozornění jako chyby" () se nepovažuje za chybu `/WX` .

- Protože MSVC zahájí implementaci funkcí z konceptu standardu C++ 20 v rámci `/std:c++latest` příznaku, `/std:c++latest` je nyní nekompatibilní s `/clr` (všechny charaktery), `/ZW` , a `/Gm` . V aplikaci Visual Studio 2019, použití `/std:c++17` nebo `/std:c++14` režimy při kompilování s `/clr` , `/ZW` , nebo `/Gm` (viz předchozí odrážka).

- U aplikací C++ pro konzoly a klasickou pracovní plochu se už negenerují předkompilované hlavičky.

### <a name="codegen-security-diagnostics-and-versioning"></a>CodeGen, zabezpečení, diagnostika a správa verzí

Vylepšená analýza s cílem `/Qspectre` zajistit pomoc při zmírnění Spectre varianty 1 (CVE-2017-5753). Další informace najdete v tématu [zmírnění hrozeb Spectre v MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).

## <a name="c-standard-library-improvements"></a>Vylepšení standardní knihovny C++

- Implementace dalších funkcí knihovny C++ 17 a C++ 20 a oprav správnosti. Podrobné informace naleznete v tématu [vylepšení shody C++ v aplikaci Visual Studio 2019](cpp-conformance-improvements.md).

- Clang – formát se pro lepší čitelnosti používá v hlavičkách standardní knihovny C++.

- Vzhledem k tomu, že Visual Studio teď podporuje Pouze můj kód pro C++, standardní knihovna už nemusí poskytovat vlastní strojní zařízení pro `std::function` a `std::visit` dosáhnout stejného účinku. Odebrání tohoto strojového zařízení do značné míry nemá žádné efekty viditelné uživatelem. Jedinou výjimkou je, že kompilátor již nebude způsobovat diagnostiku, která indikuje problémy na řádku 15732480 nebo 16707566 \< type_traits> nebo \< variant>.

## <a name="performancethroughput-improvements-in-the-compiler-and-standard-library"></a>Vylepšení výkonu a propustnosti v kompilátoru a standardní knihovně

- Vylepšení propustnosti sestavení, včetně způsobu, jakým linker zpracovává vstupně-výstupní operace se soubory, a čas propojení v typu PDB sloučení a vytváření.

- Byla přidána základní podpora pro vektory OpenMP SIMD. Můžete ji povolit pomocí nového přepínače kompilátoru **`/openmp:experimental`** . Tato možnost umožňuje, aby byly smyčky s poznámkou `#pragma omp simd` potenciálně vektorované. Není zaručeno vektorování a poznámky, které jsou opatřeny poznámkami, ale nebudou vektory, zobrazily upozornění. Nepodporují se žádné klauzule SIMD. jsou ignorovány a je hlášeno upozornění.

- Byl přidán nový přepínač příkazového řádku pro vkládání **`/Ob3`** , což je účinnější verze nástroje **`/Ob2`** . **`/O2`**(optimalizuje binární soubor pro rychlost) stále **`/Ob2`** ve výchozím nastavení implikuje. Pokud zjistíte, že kompilátor není dostatečně vložený, zvažte předání **`/O2 -Ob3`** .

- Přidali jsme podporu vnitřních funkcí SVML (Short Vector Math Library). Tyto funkce počítají hodnoty ekvivalentu bitového vektoru 128-bit, 256 nebo 512. Přidali jsme je pro podporu vektorování smyček pomocí volání funkcí matematické knihovny a určitých dalších operací, jako je celočíselné dělení. Definice podporovaných funkcí najdete v příručce [Intel Intrinsic Guide](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML).

- Nové a vylepšené optimalizace:

  - Konstantní skládání a aritmetické zjednodušení pro výrazy pomocí vnitřních vektorů SIMD pro formuláře typu float i Integer.

  - Výkonnější analýza pro extrakci informací z toku řízení (příkazy if/else/Switch) pro odebrání větví vždy ověřena jako true nebo false.

  - Vylepšené rozmemsetování pro použití instrukcí SSE2 Vector

  - Vylepšené odebrání nezbytečných kopií struktury nebo tříd, zejména pro programy v jazyce C++, které jsou předávány hodnotou.

  - Vylepšená optimalizace kódu pomocí `memmove` , například `std::copy` nebo `std::vector` a `std::string` konstrukce.

- Optimalizuje se standardní fyzický návrh knihovny, aby se předešlo kompilování částí standardní knihovny, která není přímo zahrnutá. Tato změna vyjme čas sestavení prázdného souboru, který obsahuje pouze \< vektorové> v polovině. V důsledku toho možná budete muset přidat `#include` direktivy pro hlavičky, které byly dříve nepřímo zahrnuté. Například kód, který používá, `std::out_of_range` může nyní potřebovat přidat `#include <stdexcept>` . Kód, který používá operátor vložení datového proudu, teď může být potřeba přidat `#include <ostream>` . Výhodou je, že pouze jednotky překladu ve skutečnosti používají \< stdexcept> nebo \< ostream komponenty> platíte náklady na propustnost při jejich kompilaci.

- `if constexpr`byl použit ve více místech ve standardní knihovně pro lepší propustnost a menší velikost kódu v operacích kopírování, v permutacích, jako je reverzní a otočený a v knihovně paralelních algoritmů.

- Standardní knihovna nyní používá interně `if constexpr` k omezení doby kompilace, dokonce i v režimu c++ 14.

- Detekce dynamického propojování modulu runtime pro knihovnu paralelních algoritmů již nepoužívá celou stránku k uložení pole s ukazatelem na funkci. Označení této paměti jen pro čtení bylo považováno za již nerelevantní z hlediska zabezpečení.

- `std::thread`konstruktor již nečeká na spuštění vlákna a již nebude vkládat tolik vrstev volání funkce mezi podkladovou knihovnou C `_beginthreadex` a zadaným volajícím objektem. Dřív `std::thread` Vložte šest funkcí mezi `_beginthreadex` a poskytnutý objekt, který je k dispozici. Toto číslo bylo sníženo pouze na tři, z nichž dva jsou pouze `std::invoke` . Tato změna také vyřeší chybu překrytí časování, kde `std::thread` konstruktor přestane reagovat, pokud se systémové hodiny změnily přesně v okamžiku, kdy `std::thread` byla vytvořena.

- Opravili jsme regresní regresi `std::hash` , kterou jsme představili při implementaci `std::hash<std::filesystem::path>` .

- Standardní knihovna nyní používá destruktory namísto bloků catch na několika místech pro dosažení správnosti. Tato změna vede k lepší interakci ladicího programu: výjimky, které jste vyvolali pomocí standardní knihovny v příslušných umístěních, se nyní zobrazují jako vyvolané z původní lokality throw, nikoli z našeho opětovného vyvolání. Ne všechny bloky catch knihovny Standard byly eliminovány. Očekáváme, že počet bloků catch bude v pozdějších verzích MSVC snížen.

- Neoptimální CodeGen v `std::bitset` důsledku podmíněného throw uvnitř funkce s výjimkou byla opravena rozbalením vyvolané cesty.

- `std::list`Rodina a `std::unordered_*` používá interně neladitelné iterátory na více místech.

- Několik `std::list` členů bylo změněno tak, aby opakovaně používalo seznam uzlů tam, kde je to možné, nikoli zrušením jejich přidělení a přerozdělení. Například s ohledem `list<int>` , že již má hodnotu 3, volání `assign(4, 1729)` nyní přepíše čísla v prvních třech uzlech seznamu a přidělí jeden nový uzel seznamu s hodnotou 1729.

- Všechna volání standardní knihovny `erase(begin(), end())` byla změněna na `clear()` .

- `std::vector`nyní Inicializuje a maže prvky efektivněji v určitých případech.

- Vylepšení `std::variant` , aby bylo lépe optimalizované pro optimalizaci, což vede k lepšímu vygenerování kódu. Vkládání kódu je teď mnohem lepší díky `std::visit` .

## <a name="c-ide"></a>C++ IDE

### <a name="live-share-c-support"></a>Podpora Live Share C++

[Live Share](/visualstudio/liveshare/) teď podporuje C++, což vývojářům umožňuje využívat Visual Studio nebo Visual Studio Code spolupracovat v reálném čase. Další informace najdete v tématu [oznámení Live Share pro jazyk C++: sdílení v reálném čase a spolupráce.](https://devblogs.microsoft.com/cppblog/cppliveshare/)

### <a name="intellicode-for-c"></a>IntelliCode pro C++

##### <a name="visual-studio-2019-version-161"></a> Visual Studio 2019 verze 16.1

IntelliCode používá vlastní rozsáhlé školení a váš kontext kódu k umístění toho, co je nejpravděpodobnější v horní části seznamu dokončení. Je často možné eliminovat nutnost procházení seznamu. V jazyce C++ nabízí IntelliCode největší nápovědu při používání oblíbených knihoven, jako je například standardní knihovna. IntelliCode je volitelné rozšíření, které je k dispozici v instalačním programu jako komponenta úlohy. Další informace najdete v tématu [návrhy dokončování kódu s asistencí AI přicházejí do jazyka C++ prostřednictvím IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/).

### <a name="template-intellisense"></a>IntelliSense šablony

**Panel šablon** nyní používá uživatelské rozhraní **náhledu** místo modálního okna, podporuje vnořené šablony a předem naplní všechny výchozí argumenty do **náhledu okna**. Další informace najdete v tématu [vylepšení šablon IntelliSense pro Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/template-intellisense-improvements-for-visual-studio-2019-preview-2/). Rozevírací seznam **naposledy použitých** na **panelu šablon** vám umožní rychle přepínat mezi předchozími sadami vzorových argumentů.

### <a name="new-start-window-experience"></a>Nové prostředí Start okna

Při spuštění rozhraní IDE se zobrazí nové okno Start. Obsahuje možnosti pro otevření posledních projektů, klonování kódu ze správy zdrojového kódu, otevření místního kódu jako řešení nebo složky nebo vytvoření nového projektu. Dialogové okno Nový projekt se také převedlo na funkce hledání, které by bylo možné filtrovat.

### <a name="new-names-for-some-project-templates"></a>Nové názvy pro některé šablony projektů

Změnili jsme několik názvů šablon projektů a popisy tak, aby se vešly do dialogového okna aktualizovaný nový projekt.

### <a name="various-productivity-improvements"></a>Různá vylepšení produktivity

Visual Studio 2019 obsahuje následující funkce, které vám pomůžou usnadnit a intuitivnější kódování:

- Rychlé opravy pro:
  - Přidat chybějící #include
  - NULL na nullptr
  - Přidat chybějící středník
  - Vyřešit chybějící obor názvů nebo obor
  - Nahradit chybné operandy indirekce ( \* pro & a & na \* )
- Rychlé informace o bloku najetím myší na pravou složenou závorku
- Náhled souboru hlaviček nebo kódu
- Přejít k definici při #include otevře soubor

Další informace najdete v tématu [vylepšení produktivity C++ v aplikaci Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/c-productivity-improvements-in-visual-studio-2019-preview-2/).

### <a name="quickinfo-improvements"></a>Vylepšení QuickInfo

##### <a name="visual-studio-2019-version-161"></a> Visual Studio 2019 verze 16.1

Rychlé informace nyní dodržuje sémantickou zabarvení editoru. Má také nový odkaz **Search online** , který vyhledá online dokumenty, kde najdete další informace o konstrukci kódu na pojetí. Odkaz, který poskytuje rychlé informace pro kód s červenou vlnovkou, bude hledat chybu online. Tímto způsobem není nutné znovu zadávat zprávu do prohlížeče. Další informace naleznete v tématu [rychlá vylepšení informací v aplikaci Visual Studio 2019: zabarvení a hledání online](https://devblogs.microsoft.com/cppblog/quick-info-improvements-in-visual-studio-2019-colorization-and-search-online/).

### <a name="intellicode-available-in-c-workload"></a>IntelliCode k dispozici v úlohách C++

##### <a name="visual-studio-2019-version-161"></a> Visual Studio 2019 verze 16.1

IntelliCode se teď dodává jako volitelná součást pro **desktopovou vývoj s** využitím úlohy C++. Další informace najdete v tématu [vylepšené C++ IntelliCode nyní dodávané se sadou Visual Studio 2019](https://devblogs.microsoft.com/cppblog/improved-c-intellicode-now-ships-with-visual-studio-2019/).

## <a name="cmake-support"></a>Podpora CMake

- Podpora CMake 3,14

- Sada Visual Studio nyní může otevřít existující mezipaměti CMake generované externími nástroji, jako je CMakeGUI, přizpůsobené systémy meta-buildu nebo skripty sestavení, které spouštějí cmake. exe samotné.

- Vylepšený výkon technologie IntelliSense.

- Nový editor nastavení poskytuje alternativu k ruční úpravě souboru CMakeSettings. JSON a poskytuje určitou paritu s CMakeGUI.

- Visual Studio vám pomůže rozběhnout vývoj v jazyce C++ s nástroji CMake na Linuxu díky rozpoznání, jestli máte na počítači s Linuxem kompatibilní verzi CMake. Pokud ne, aplikace vám nabídne její instalaci.

- Nekompatibilní nastavení v CMakeSettings, jako jsou neshodné architektury nebo nekompatibilní nastavení generátoru CMake, zobrazují v editoru JSON vlnové hodnoty a chyby v seznamu chyb.

- Po spuštění příkazu `vcpkg integrate install` se automaticky rozpozná sada nástrojů vcpkg a povolí se pro projekty CMake, které jsou otevřené v integrovaném vývojovém prostředí. Toto chování můžete vypnout tak, že v nástroji CMakeSettings zadáte prázdný soubor sady nástrojů.

- Projekty CMake teď ve výchozím nastavení aktivují ladění s možností Pouze můj kód.

- Upozornění na statickou analýzu se teď zpracovávají na pozadí a zobrazují se v editoru projektů CMake.

- Vymažte sestavení a nakonfigurujte zprávy Begin a end pro projekty CMake a podporu uživatelského rozhraní pro průběh sestavení sady Visual Studio. Kromě toho je teď nastavení podrobností CMake v **nabídce nástroje > možnosti** přizpůsobení úrovně podrobností pro zprávy o sestavení a konfiguraci cmake v okno výstup.

- Toto `cmakeToolchain` nastavení se teď v CMakeSettings. JSON podporuje, pokud chcete zadat sady nástrojů, aniž byste museli ručně upravovat příkazový řádek cmake.

- Novou zkratku nabídky **sestavit vše** **CTRL + SHIFT + B**.

##### <a name="visual-studio-2019-version-161"></a> Visual Studio 2019 verze 16.1

- Integrovaná podpora pro úpravy, sestavování a ladění projektů CMake s využitím Clang/LLVM. Další informace naleznete v tématu [Podpora Clang/LLVM v aplikaci Visual Studio](https://devblogs.microsoft.com/cppblog/clang-llvm-support-in-visual-studio/).

## <a name="linux-and-the-windows-subsystem-for-linux"></a>Linux a subsystém Windows pro Linux

##### <a name="visual-studio-2019-version-161"></a> Visual Studio 2019 verze 16.1

- Podpora [AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) v projektech pro Linux a cmake v různých platformách. Další informace najdete v tématu [AddressSanitizer (ASan) pro úlohu Linux v aplikaci Visual Studio 2019](https://devblogs.microsoft.com/cppblog/addresssanitizer-asan-for-the-linux-workload-in-visual-studio-2019/).

- Integrovaná podpora sady Visual Studio pro použití jazyka C++ se subsystémem Windows pro Linux (WSL). Další informace naleznete v tématu [C++ pomocí sady Visual Studio 2019 a subsystému Windows pro Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

## <a name="incredibuild-integration"></a>Integrace IncrediBuild

IncrediBuild je zahrnuta jako volitelná součást při **vývoji desktopových** aplikací v C++. Monitor sestavení IncrediBuild je plně integrovaný v integrovaném vývojovém prostředí sady Visual Studio. Další informace naleznete v tématu [vizualizace sestavení pomocí monitoru sestavení IncrediBuild a sady Visual Studio 2019](https://devblogs.microsoft.com/cppblog/visualize-your-build-with-incredibuilds-build-monitor-and-visual-studio-2019/).

## <a name="debugging"></a>Ladění

- Pro aplikace C++ běžící ve Windows se soubory PDB nyní načítají v samostatném 64 procesu. Tato změna řeší řadu havárií způsobenou nedostatku paměti ladicího programu. Například při ladění aplikací, které obsahují velký počet modulů a souborů PDB.

- Hledání je povolené v oknech **kukátko**, **Automatické**hodnoty a **místní** hodnoty.

## <a name="windows-desktop-development-with-c"></a>Vývoj desktopových aplikací pro Windows pomocí C++

- Tito průvodci ATL/MFC knihovny C++ již nejsou k dispozici:

  - Průvodce komponentami ATL COM+ 1.0
  - Průvodce komponentami ATL Active Server Pages
  - Průvodce zprostředkovatelem ATL OLE DB
  - Průvodce stránkou vlastností ATL
  - Průvodce příjemcem ATL OLE DB
  - Příjemce knihovny MFC rozhraní ODBC
  - Třída MFC z ovládacího prvku ActiveX
  - Třída MFC z knihovny typů.

  Ukázkový kód pro tyto technologie je archivován v Microsoft Docs a v úložišti GitHub VCSamples.

- Sada Windows 8.1 Software Development Kit (SDK) již není v instalačním programu sady Visual Studio k dispozici. Doporučujeme upgradovat projekty C++ na nejnovější sadu Windows 10 SDK. Pokud někde používáte pevnou závislost na sadě Windows 8.1 SDK, můžete si ji stáhnout z archivu sad Windows SDK.

- V nejnovější sadě nástrojů C++ už nebude k dispozici cílení na Windows XP. Cílení na XP s & kompilátory MSVC kompilátoru VS 2017 se pořád podporuje a dají se nainstalovat prostřednictvím "jednotlivých komponent".

- Naše dokumentace aktivně odrazuje od používání slučovacích modulů k nasazení modulu Runtime Visual C++. V tomto dodatečném kroku vybereme tento produkt, který označuje naše MSMs jako zastaralé. Zvažte migraci centrálního nasazení VCRuntime z balíčků MSM na balíček opětovné distribuce.

## <a name="mobile-development-with-c-android-and-ios"></a>Vývoj pro mobilní zařízení v C++ (Android a iOS)

Výchozím prostředím C++ Android je nyní Android SDK 25 a Android NDK 16b.

## <a name="clangc2-platform-toolset"></a>Sada nástrojů platformy Clang/C2

Experimentální součást Clang/C2 se odebrala. Použijte sadu nástrojů MSVC pro úplnou shodu standardů C++ s `/permissive-` a `/std:c++17` , nebo CLANG/LLVM sada nástrojů pro Windows.

## <a name="code-analysis"></a>Analýza kódu

- Analýza kódu se teď spouští automaticky na pozadí. Upozornění se v editoru během psaní podtrhávají zelenou vlnovkou. Další informace naleznete v tématu [Analýza kódu v editoru v aplikaci Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/in-editor-code-analysis-in-visual-studio-2019-preview-2/).

- Nová experimentální pravidla ConcurrencyCheck pro dobře známé standardní typy knihoven z \< hlavičky mutex>. Další informace naleznete v tématu [Analýza kódu souběžnosti v aplikaci Visual Studio 2019](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/).

- Aktualizovaná Částečná implementace [kontroly profilu životnosti](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/), která detekuje ukazatele dangling a odkazy. Další informace najdete v tématu [aktualizace profilu životnosti v aplikaci Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/).

- Další kontroly související s korutinou, včetně C26138, C26810, C26811 a experimentálního pravidla C26800. Další informace naleznete v tématu [nové kontroly analýzy kódu v aplikaci Visual Studio 2019: použití za přesunutí a korutina](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/).

##### <a name="visual-studio-2019-version-161"></a> Visual Studio 2019 verze 16.1

- Nové rychlé opravy pro neinicializované kontroly proměnných. Další informace najdete v tématu [nové opravy pro analýzu kódu pro neinicializovaná paměť (C6001) a použití před upozorněními init (C26494)](https://devblogs.microsoft.com/cppblog/new-code-analysis-quick-fixes-for-uninitialized-memory-c6001-and-use-before-init-c26494-warnings/).

## <a name="unit-testing"></a>Testování jednotek

Šablona spravovaného testovacího projektu C++ už není dostupná. Můžete pokračovat v používání spravovaného testovacího rozhraní jazyka C++ v existujících projektech. Pro nové testy jednotek zvažte použití jednoho z nativních testovacích rozhraní, pro které aplikace Visual Studio poskytuje šablony (MSTest, Google Test), nebo šablonu spravovaného testovacího projektu jazyka C#.

::: moniker-end

::: moniker range="=vs-2017"

Visual Studio 2017 přináší mnoho aktualizací a oprav prostředí C++. Opravili jsme víc než 250 chyb a nahlášených problémů v kompilátoru a nástrojích. Mnoho poslali zákazníci prostřednictvím [nahlášení problému a](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2017) v rámci **odesílání názorů**poskytli možnosti návrhů. Děkujeme vám, že hlásíte chyby! Další informace o tom, co je nového ve všech verzích sady Visual Studio, naleznete v tématu [co je nového v aplikaci Visual studio 2017](/visualstudio/ide/whats-new-visual-studio-2017?view=vs-2017). Informace o novinkách jazyka C++ v aplikaci Visual Studio 2019 naleznete v tématu [co je nového pro jazyk c++ v aplikaci Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019). Informace o tom, co je nového v jazyce C++ v aplikaci Visual Studio 2015 a starších verzích, najdete v tématu [Visual C++ novinky 2003 až 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="visual-studio-2017-c-compiler"></a>Visual Studio 2017 C++ – kompilátor

### <a name="c-conformance-improvements"></a>Vylepšení shody C++

V této verzi jsme aktualizovali kompilátor C++ a standardní knihovnu s rozšířenou podporou pro funkce C++ 11 a C++ 14. Zahrnuje taky předběžnou podporu pro některé funkce očekávané ve standardu C++ 17. Podrobné informace naleznete v tématu [vylepšení shody C++ v aplikaci Visual Studio 2017](cpp-conformance-improvements.md).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

Kompilátor podporuje přibližně 75% funkcí, které jsou v C++ 17 novinkou, včetně strukturovaných vazeb, `constexpr` výrazů lambda, `if constexpr` , vložených proměnných, výrazů skládání a přidávání `noexcept` do systému typů. Tyto funkce jsou k dispozici v rámci **`/std:c++17`** Možnosti. Další informace naleznete v tématu [vylepšení shody C++ v aplikaci Visual Studio 2017](cpp-conformance-improvements.md) .

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

Sada nástrojů kompilátoru MSVC v sadě Visual Studio verze 15,7 teď vyhovuje standardu C++. Další informace naleznete v tématu [oznamujeme: MSVC odpovídá standardu c++](https://devblogs.microsoft.com/cppblog/announcing-msvc-conforms-to-the-c-standard/) a [souladu s jazykem Microsoft C++](../visual-cpp-language-conformance.md).

##### <a name="visual-studio-2017-version-158"></a>Visual Studio 2017 verze 15,8

[`/experimental:preprocessor`](../build/reference/experimental-preprocessor.md)Přepínač kompilátoru umožňuje nový experimentální preprocesor MSVC, který bude nakonec odpovídat všem použitelným normám jazyka C a C++. Další informace najdete v tématu [MSVC experimentální preprocesor – přehled](../preprocessor/preprocessor-experimental-overview.md).

### <a name="new-compiler-options"></a>Nové možnosti kompilátoru

- [`/permissive-`](../build/reference/permissive-standards-conformance.md): Povolte všechny možnosti kompilátoru s přísnými standardy a zakažte většinu rozšíření kompilátoru specifických pro společnost Microsoft (ale ne `__declspec(dllimport)` , například). Tato možnost je ve výchozím nastavení zapnuta v aplikaci Visual Studio 2017 verze 15,5.  **`/permissive-`** Režim shody zahrnuje podporu vyhledávání názvů se dvěma fázemi. Další informace naleznete v tématu [vylepšení shody C++ v aplikaci Visual Studio](cpp-conformance-improvements.md).

- [`/diagnostics`](../build/reference/diagnostics-compiler-diagnostic-options.md): Povoluje zobrazení diagnostické chyby nebo místa upozornění třemi různými způsoby: pouze číslo řádku, číslo řádku a sloupec nebo číslo řádku a sloupec se blikajícím kurzorem pod problematickým řádkem kódu.

- [`/debug:fastlink`](../build/reference/debug-generate-debug-info.md): Můžete povolit až 30% rychlejších přírůstkových propojení (vs. Visual Studio 2015) tak, že všechny informace o ladění nekopírujete do souboru PDB. Soubor PDB místo toho odkazuje na ladicí informace pro objekty a soubory knihovny použité k vytvoření spustitelného souboru. Podívejte se na [rychlejší cyklus sestavení c++ v vs "15 `/Debug:fastlink` " s](https://devblogs.microsoft.com/cppblog/faster-c-build-cycle-in-vs-15-with-debugfastlink/) [doporučeními a urychlíte sestavení v jazyce C++ v sadě Visual Studio](https://devblogs.microsoft.com/cppblog/recommendations-to-speed-c-builds-in-visual-studio/).

- Visual Studio 2017 umožňuje používat [`/sdl`](../build/reference/sdl-enable-additional-security-checks.md) s [`/await`](../build/reference/await-enable-coroutine-support.md) . Odebrali jsme [`/RTC`](../build/reference/rtc-run-time-error-checks.md) omezení s korutinami.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

- [ `/std:c++14` a `/std:c++latest` ](../build/reference/std-specify-language-standard-version.md): tyto možnosti kompilátoru vám umožňují vyjádřit výslovný souhlas s konkrétní verzí programovacího jazyka ISO C++ v projektu. Většina nových konceptů nových funkcí je chráněná **`/std:c++latest`** možností.

- [`/std:c++17`](../build/reference/std-specify-language-standard-version.md)povoluje sadu funkcí C++ 17 implementovaných kompilátorem. Tato možnost zakazuje podporu kompilátoru a standardní knihovny pro funkce po C++ 17: ty, které se změnily nebo novinují v novějších verzích pracovní verze a aktualizace chyb standardu C++. Pokud chcete tyto funkce povolit, použijte **`/std:c++latest`** .

### <a name="codegen-security-diagnostics-and-versioning"></a>CodeGen, zabezpečení, diagnostika a správa verzí

Tato vydaná verze přináší několik vylepšení optimalizace, generování kódu, správu verzí sady nástrojů a diagnostiku. Mezi důležitá vylepšení patří:

- Vylepšené generování kódu smyček: Podpora automatické vektorizace dělení konstantních celých čísel, lepší identifikace vzorů memset
- Vylepšené zabezpečení kódu: Vylepšená emise diagnostiky kompilátoru přetečení vyrovnávací paměti a [`/guard:cf`](../build/reference/guard-enable-control-flow-guard.md) teď chrání příkazy Switch, které generují tabulky skoků.
- Správa verzí: v každé Visual C++ aktualizace sady nástrojů se nyní aktualizuje hodnota předdefinovaného předběžného makra ** \_ MSC \_ ver** . Další informace naleznete v tématu [Visual C++ verze kompilátoru](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/).
- Nové rozložení sady nástrojů: kompilátor a související nástroje sestavení mají na svém vývojovém počítači nové umístění a strukturu adresářů. Nové rozložení umožňuje souběžnou instalaci více verzí kompilátoru. Další informace naleznete v tématu [rozložení nástrojů kompilátoru v aplikaci Visual Studio 2017](https://devblogs.microsoft.com/cppblog/compiler-tools-layout-in-visual-studio-15/).
- Vylepšená diagnostika: okno výstup nyní zobrazuje sloupec, ve kterém došlo k chybě. Další informace naleznete v tématu [vylepšení diagnostiky kompilátoru C++ v sadě vs "15" Preview 5](https://devblogs.microsoft.com/cppblog/c-compiler-diagnostics-improvements-in-vs-15-rc/).
- Při použití korutiny je možné odebrat experimentální **klíčové slovo** (k dispozici v **`/await`** Možnosti). Váš kód by měl být aktualizován, aby bylo možné použít `co_yield` místo toho. Další informace najdete v tématu [ `yield` klíčové slovo, které se má `co_yield` v vs 2017](https://devblogs.microsoft.com/cppblog/yield-keyword-to-become-co_yield-in-vs-2017/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

Další vylepšení diagnostiky v kompilátoru. Další informace najdete v tématu [vylepšení diagnostiky v aplikaci Visual Studio 2017 15.3.0](https://devblogs.microsoft.com/cppblog/diagnostic-improvements-in-vs2017-15-3-0/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

Visual C++ výkon modulu runtime dál vylepšuje prostřednictvím lepší kvality vygenerovaného kódu. Nyní můžete znovu kompilovat kód a aplikace je spouštěna rychleji. Některé optimalizace kompilátoru jsou zcela nové, například vektory podmíněných skalárních úložišť, kombinování volání `sin(x)` a `cos(x)` nové `sincos(x)` a eliminují redundantní pokyny z Optimalizátoru SSA. Další optimalizace kompilátoru jsou vylepšení stávající funkce, jako například: vektorizace heuristiky pro podmíněné výrazy, lepší optimalizace smyček a minimální CodeGen na maximum. Linker má novou a rychlejší **`/OPT:ICF`** implementaci, což může způsobit až 9% urychleníí času propojení a další opravy výkonu v přírůstkovém propojování. Další informace najdete v tématu [/opt (optimalizace)](../build/reference/opt-optimizations.md) a [/incremental (propojování přírůstkově)](../build/reference/incremental-link-incrementally.md).

Kompilátor Microsoft C++ podporuje Intel AVX-512. Obsahuje pokyny pro délku vektoru, které přinášejí nové funkce v AVX-512 až 128 bitů a 256 bitů v registru.

Parametr [/Zc: noexceptTypes-](../build/reference/zc-noexcepttypes.md) lze použít pro návrat k verzi c++ 14, `noexcept` zatímco obecně používá režim c++ 17. Tato možnost umožňuje aktualizovat zdrojový kód tak, aby odpovídal C++ 17 bez nutnosti přepsat celý `throw()` kód současně. Další informace naleznete v tématu [odstranění specifikace dynamické výjimky a s výjimkou](cpp-conformance-improvements.md#noexcept_removal).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

- Nový přepínač kompilátoru [/Qspectre](../build/reference/qspectre.md) , který se může zmírnit proti spekulativním útokům na straně vykonání kanálu. Další informace najdete v tématu [zmírnění hrozeb Spectre v MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).
- Nové diagnostické upozornění pro zmírnění rizik Spectre Další informace najdete v tématu [Diagnostika Spectre ve Visual studiu 2017 verze 15,7 Preview 4](https://devblogs.microsoft.com/cppblog/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/).
- Nová hodnota parametru/Zc, **`/Zc:__cplusplus`** umožňuje správné vytváření sestav standardní podpory jazyka C++. Například když je přepínač nastaven a kompilátor je v režimu, hodnota se **`/std:c++17`** rozšíří na **`201703L`** . Další informace najdete v článku [MSVC nyní správně hlásí __cplusplus](https://devblogs.microsoft.com/cppblog/msvc-now-correctly-reports-__cplusplus/).

## <a name="c-standard-library"></a>Standardní knihovna C++

### <a name="correctness-improvements"></a>Vylepšení správnosti

##### <a name="visual-studio-2017-rtm-version-150"></a>Visual Studio 2017 RTM (verze 15,0)

- Menší `basic_string` `_ITERATOR_DEBUG_LEVEL != 0` vylepšení diagnostiky. Když je v řetězcovém strojovém stroji Trip, bude nyní hlásit konkrétní chování, které způsobilo cestu. Například místo zprávy oznamující, že iterátor řetězce nejde přesměrovat, se teď zobrazí zpráva s oznámením, že iterátor řetězce nejde přesměrovat, protože je mimo rozsah (např. je to koncový iterátor).
- Opravili jsme `std::promise` operátor přiřazení přesunutí, který dřív mohl způsobit, že se kód trvale zablokuje.
- Opravily se chyby kompilátoru s `atomic<T*>` implicitním převodem na `T*` .
- `pointer_traits<Ptr>`nyní správně detekuje `Ptr::rebind<U>` .
- Opravili chybějící `const` kvalifikátor v `move_iterator` operátoru odčítání.
- Opravili jsme tiché chybné CodeGen pro stavová uživatelem definovaná přidělování, která vyžadují `propagate_on_container_copy_assignment` a `propagate_on_container_move_assignment` .
- `atomic<T>`Nyní je tolerována přetížení `operator&()` .
- Mírně Vylepšená Diagnostika kompilátoru pro nesprávná `bind()` volání.

V aplikaci Visual Studio 2017 RTM existuje více standardních vylepšení knihovny. Úplný seznam najdete v tématu věnovaném standardům blogu týmu C++ [v sadě VS 2017 RTM o opravách standardní knihovny](https://devblogs.microsoft.com/cppblog/stl-fixes-in-vs-2017-rtm/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

- Knihovny standardních knihoven teď připnuté `max_size()` na `numeric_limits<difference_type>::max()` místo `max()` `size_type` . Tato změna zajišťuje, že výsledek z `distance()` iterátorů z tohoto kontejneru je reprezentovatelné v návratovém typu `distance()` .
- Pevná `auto_ptr<void>` chybějící specializace
- `for_each_n()`Předtím, než je `generate_n()` `search_n()` argument Length celočíselný typ, se nepodařilo kompilovat algoritmy, a. Nyní se pokusí převést neintegrální délky na iterátory `difference_type` .
- `normal_distribution<float>`už negeneruje upozornění uvnitř standardní knihovny o zúžení z Double na float.
- Opravili jsme některé `basic_string` operace, které se `npos` místo toho používaly `max_size()` při kontrole maximální velikosti přetečení.
- `condition_variable::wait_for(lock, relative_time, predicate)`by čekal na celou relativní dobu, pokud došlo k spuriousmu probuzení. Nyní čeká pouze na jeden interval relativního času.
- `future::get()`teď neověřuje `future` , jak vyžaduje standard.
- `iterator_traits<void *>`používá se k tomu, že došlo k závažné chybě, protože se pokusila o vystavení `void&` . teď se z ní čistí prázdná struktura, aby se povolilo použití `iterator_traits` v podmínkách SFINAE typu "je iterátor".
- Některá upozornění oznámená Clang **-Wsystem-Headers** byla opravena.
- Také opravená "specifikace výjimky v deklaraci neodpovídá předchozí deklaraci" hlášené pomocí Clang **-Wmicrosoft-Exception-spec**.
- Také opravená upozornění na řazení mem-inicializátor-list hlášená Clang a C1XX.
- Neuspořádané kontejnery neměnily své funkce hash nebo predikáty, pokud byly samotné kontejnery prohozeny. Teď to dělají.
- Teď je označená spousta operací prohození kontejnerů `noexcept` (protože naše standardní knihovna nikdy nechce vyvolat výjimku při zjišťování `propagate_on_container_swap` nedefinované podmínky nedefinovaného nedefinovaného přidělujícího modulu, který nerovná se).
- Mnoho `vector<bool>` operací je nyní označeno `noexcept` .
- Standardní knihovna nyní vynutilí odpovídajícího přidělování `value_type` (v režimu c++ 17) s řídicím šrafováním pro výslovný souhlas.
- Opravili jsme některé podmínky, kdy by se v rámci sebe do rozsahu vložení do sebe `basic_string` zaznamenal obsah řetězců. (Poznámka: pole pro vložení do rozsahu je stále zakázáno standardem.)
- `basic_string::shrink_to_fit()`už není ovlivněný přidělováním `propagate_on_container_swap` .
- `std::decay`nyní zpracovává typy funkcí Abominable, tj. typy funkcí, které jsou kvalifikovány na základě CV, nebo obojí.
- Změněné direktivy include pro použití správných citlivostí velkých a malých písmen a lomítka, zlepšení přenositelnosti.
- Pevné upozornění C4061 "enumerátor '*enumerátor*' v přepínači*výčtu ' enum ' není*explicitně zpracováno jmenovkou Case". Toto upozornění je vypnuto – ve výchozím nastavení a bylo opraveno jako výjimka pro obecné zásady standardní knihovny pro upozornění. (Standardní knihovna je **`/W4`** čistá, ale nepokusí se **`/Wall`** vyčistit. Mnohé z nestandardních upozornění jsou většinou nenáročné na vysokou úroveň a nejsou určeny pro pravidelné používání.)
- Vylepšené `std::list` kontroly ladění. Seznam iterátorů nyní kontroluje `operator->()` a `list::unique()` nyní označuje iterátory jako neověřené.
- Pevná použití metaprogramování šablonou pro přidělování v `tuple` .

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- `std::partition`nyní `N` namísto času volá predikát `N + 1` , jak vyžaduje standard.
- Pokusy o zamezení Magic static ve verzi 15,3 byly opraveny ve verzi 15,5.
- `std::atomic<T>`již není nutné `T` používat výchozí constructible.
- Algoritmy haldy, které přijímají logaritmické časy, se chovají jinak, když je povoleno ladění iterátoru. Již nedělají lineární časový kontrolní výraz, že vstup je ve skutečnosti halda.
- `__declspec(allocator)`je teď chráněná jenom pro C1XX, aby se zabránilo varováním z Clang, které nerozumí tomuto declspec.
- `basic_string::npos`je nyní k dispozici jako časová konstanta kompilace.
- `std::allocator`v režimu C++ 17 nyní správně zpracovává přidělení nadrovnaných typů, to znamená typy, jejichž zarovnání je větší než `max_align_t` , pokud není zakázáno **`/Zc:alignedNew-`** .  Například vektory objektů se zarovnáním na 16 bajtů nebo 32 bajtů jsou nyní správně zarovnány pro instrukce SSE a AVX.

### <a name="conformance-improvements"></a>Vylepšení shody

- Přidali jsme \< \> \< string_view \> , `apply()` , `make_from_tuple()` .
- Přidání \< Optional \> , \< variant \> , `shared_ptr::weak_type` a \< cstdalign \> .
- Povoleno C++ 14 `constexpr` v `min(initializer_list)` , `max(initializer_list)` ,, `minmax(initializer_list)` a `min_element()` `max_element()` , a `minmax_element()` .

Další informace najdete v [tabulce pro shodu jazyka Microsoft C++](../visual-cpp-language-conformance.md).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

- Bylo implementováno několik dalších funkcí C++ 17. Další informace najdete v [tabulce pro shodu jazyka Microsoft C++](cpp-conformance-improvements.md#improvements_153).
- Implementovaná P0602R0a "variant a Optional by měla rozšířit triviální možnost kopírování/přesunutí".
- Standardní knihovna nyní umožňuje úředně tolerovat dynamickou RTTI zakázanou prostřednictvím možnosti [/gr-](../build/reference/gr-enable-run-time-type-information.md) . Obě `dynamic_pointer_cast()` i `rethrow_if_nested()` `dynamic_cast` z nich vyžadují, aby ji standardní knihovna nyní vyznačuje jako `=delete` v rámci **`/GR-`** .
- I v případě, že byl dynamický RTTI zakázán prostřednictvím **`/GR-`** , je "statický RTTI" ve formě `typeid(SomeType)` stále k dispozici a má několik standardních komponent knihovny. Standardní knihovna teď podporuje i vypnutí této funkce prostřednictvím **`/D_HAS_STATIC_RTTI=0`** . Tento příznak také zakáže `std::any` , `target()` a `target_type()` členské funkce a členské `std::function` `get_deleter()` funkce `std::shared_ptr` `std::weak_ptr` typu a.
- Standardní knihovna nyní používá C++ 14 `constexpr` nepodmíněný, namísto podmíněně definovaných maker.
- Standardní knihovna nyní používá šablony aliasu interně.
- Standardní knihovna nyní používá `nullptr` interně místo `nullptr_t{}` . (Bylo vyhubeno vnitřní použití hodnoty NULL. Vnitřní použití 0-as-null se vyčistí postupně.)
- Standardní knihovna nyní používá `std::move()` interně místo stylistických nepoužívání `std::forward()` .
- Změněno `static_assert(false, "message")` na `#error message` . Tato změna vylepšuje diagnostiku kompilátoru `#error` , protože okamžitě zastaví kompilaci.
- Standardní knihovna již neoznačuje funkce jako `__declspec(dllimport)` . Technologie moderního linkeru už to nevyžaduje.
- Extrahována SFINAE k výchozím argumentům šablony, což snižuje množství zbytečných hodnot v porovnání s návratovými typy a typy argumentů funkce.
- Kontroly ladění v \< náhodných \> verzích teď místo interní funkce `_Rng_abort()` , která se volá `fputs()` do **stderr**, používají běžné strojní zařízení standardní knihovny. Implementace této funkce byla zachovaná kvůli binární kompatibilitě. Odebereme ho v další binární a nekompatibilní verzi standardní knihovny.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- Některé funkce standardní knihovny byly přidány, zastaralé nebo odebrané podle standardu C++ 17. Další informace naleznete v tématu [vylepšení shody C++ v aplikaci Visual Studio](cpp-conformance-improvements.md#improvements_155).
- Experimentální podpora těchto paralelních algoritmů:
  - `all_of`
  - `any_of`
  - `for_each`
  - `for_each_n`
  - `none_of`
  - `reduce`
  - `replace`
  - `replace_if`
  - `sort`
- Signatury pro následující paralelní algoritmy jsou přidány, ale nejsou v tuto chvíli paralelní. Profilace ukázala, že v algoritmech virtuálního nejsou žádné výhody, které přesouvají nebo permute – prvky:
  - `copy`
  - `copy_n`
  - `fill`
  - `fill_n`
  - `move`
  - `reverse`
  - `reverse_copy`
  - `rotate`
  - `rotate_copy`
  - `swap_ranges`

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 verze 15.6

- \<memory_resource>
- Základy knihovny v1
- Odstraňuje se `polymorphic_allocator` přiřazení
- Vylepšení srážek argumentu šablony třídy

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

- Podpora paralelních algoritmů už není experimentální.
- Nová implementace \<> systému souborů
- Základní převody řetězců (částečné)
- `std::launder()`
- `std::byte`
- `hypot(x,y,z)`
- Předcházení zbytečným Decay
- Matematické speciální funkce
- `constexpr char_traits`
- Průvodci odpočty pro standardní knihovnu

Další informace najdete v [tabulce pro shodu jazyka Microsoft C++](../visual-cpp-language-conformance.md).

### <a name="performance-and-throughput-fixes"></a>Opravy výkonu a propustnosti

- Převedená `basic_string::find(char)` přetížení se volají jenom `traits::find` jednou. Dříve byla implementována jako obecná řetězcová hledání pro řetězec o délce 1.
- `basic_string::operator==`nyní před porovnáváním obsahu řetězců kontroluje velikost řetězce.
- Bylo odebráno propojení ovládacího prvku v `basic_string` , což bylo pro Optimalizátor kompilátoru obtížné analyzovat. U všech krátkých řetězců volání `reserve` stále obsahuje nenulové náklady, aby nedošlo k žádné akci.
- `std::vector`se převedlo na správnost a výkon: vytváření aliasů během operací vložení a emplace je teď správně zpracované podle požadavků standardu. Záruka silné výjimky je teď k dispozici v případě, že je to vyžadováno standardem Via `move_if_noexcept()` a jinou logikou a vkládat a emplace méně operací elementu.
- Standardní knihovna C++ teď nevylučuje přesměrování na ozdobné ukazatele s hodnotou null.
- Vylepšený `weak_ptr::lock()` výkon.
- Pro zvýšení propustnosti kompilátoru teď hlavičky standardní knihovny C++ nepoužívejte deklarace pro nepotřebné vnitřní funkce kompilátoru.
- Vylepšený výkon `std::string` a `std::wstring` Přesun konstruktorů více než třikrát.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

- Spolupracovaly s interakcemi `noexcept` , které zabraňují vkládání `std::atomic` implementace do funkcí, které používají strukturované zpracování výjimek (SEH).
- Byla změněna interní funkce standardní knihovny `_Deallocate()` pro optimalizaci do menšího kódu, což umožňuje jejich inlineování na více místech.
- Změněno `std::try_lock()` na použití rozšíření balíčku namísto rekurze.
- Vylepšený `std::lock()` algoritmus pro zamezení zablokování pro použití `lock()` operací místo odstřeďování na `try_lock()` všech zámkech.
- Byla povolena optimalizace pojmenované návratové hodnoty v `system_category::message()` .
- `conjunction`a `disjunction` nyní vytváří instanci `N + 1` typů namísto `2N + 2` typů.
- `std::function`již nevytváří instance pro každý typ, který je vyměnitelný, a zlepšuje propustnost a snižuje velikost objektu. obj v programech, které předají mnoho různých výrazů lambda `std::function` .
- `allocator_traits<std::allocator>`obsahuje ručně vložené `std::allocator` operace, zmenšení velikosti kódu v kódu, který komunikuje `std::allocator` `allocator_traits` pouze prostřednictvím pouze (to znamená ve většině kódu).
- Rozhraní s minimálním přihlašováním v jazyce C++ 11 je nyní zpracováváno pomocí standardní knihovny volání `allocator_traits` přímo místo zabalení přidělujícího modulu do interní třídy `_Wrap_alloc` . Tato změna snižuje velikost kódu vygenerovaného pro podporu přidělování, zlepšuje v některých případech schopnost Optimalizátoru na základě knihoven standardních knihoven a poskytuje lepší možnosti ladění (jak je nyní zobrazen typ přidělování, nikoli `_Wrap_alloc<your_allocator_type>` v ladicím programu).
- Odebrali jsme metaprogramování šablonou pro přizpůsobená nastavení `allocator::reference` , která přidělování nemůžou přizpůsobit. (Alokátory můžou kontejnery používat ozdobné ukazatele, ale ne ozdobné odkazy.)
- Front-end kompilátor byl výukou pro rozbalení iterátorů ladění v rámci smyček na základě rozsahu, což vylepšuje výkon sestavení ladění.
- `basic_string`Interní cesta zmenšení pro `shrink_to_fit()` a již `reserve()` není v cestě k přerozdělení operací, čímž se zmenší velikost kódu pro všechny ostatní členy.
- `basic_string`Interní cesta zvětšení již není v cestě k umístění `shrink_to_fit()` .
- Tyto `basic_string` operace jsou nyní přizpůsobené nepřidělením rychlé cesty a přidělení funkcí pomalých cest. díky tomu je pravděpodobnější, že běžný případ bez opětovného přidělení nebude zapsaný do volajících.
- `basic_string`Mutace operace nyní vytvoří znovu přidělené vyrovnávací paměti v upřednostňovaném stavu, nikoli při změně velikosti. Například vložení na začátku řetězce nyní přesune obsah po vložení přesně jednou. Přesune se buď dolů, nebo do nově přidělené vyrovnávací paměti. V opačném případě se už nepřesouvá dvakrát v případě, že se napředuje nově přidělená vyrovnávací paměť a pak se dolů.
- Operace, které volají standardní knihovnu jazyka C v \< řetězci \> nyní `errno` mají v mezipaměti adresu pro odebrání opakované interakce s protokolem TLS.
- Zjednodušená `is_pointer` implementace.
- Změna výrazu založeného na funkci SFINAE na `struct` a `void_t` na základě.
- Standardní algoritmy knihovny nyní zabraňují iterátorům postincrementing.
- Pevná upozornění zkrácení při použití 32ho přidělování bitů na 64 systémech.
- `std::vector`přiřazení přesunutí je teď v případě, že je to možné, v případě, že je to možné, i v případě, že je to možné, v opačném případě nePOCMAm

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- `basic_string<char16_t>`nyní zahájí stejnou `memcmp` , `memcpy` a podobnou optimalizaci, která se `basic_string<wchar_t>` zabývá.
- Omezení Optimalizátoru, které zabránilo vloženému ukazatelům na funkce, je zveřejněné v aplikaci Visual Studio 2015 Update 3, se kterými se obnovil výkon `lower_bound(iter, iter, function pointer)` .
- Režie pro ověření vstupu na základě pořadí ladění iterátoru u vstupů do `includes` , `set_difference` , `set_symmetric_difference` a `set_union` byla snížena pomocí rozbalení iterátorů před ověřením pořadí.
- `std::inplace_merge`nyní přeskočí nad prvky, které již jsou na pozici.
- Sestavování již `std::random_device` není konstrukce a poté zničení `std::string` .
- `std::equal`a `std::partition` měl průchod s optimalizací pro dělení na vlákna, který ukládá porovnání iterátoru.
- Když `std::reverse` je předána ukazatelům na triviální kopii `T` , bude nyní zaslána do ručně určené vektorové implementace.
- `std::fill`, `std::equal` a `std::lexicographical_compare` byly výukou, jak odesílat do `memset` a `memcmp` pro `std::byte` a `gsl::byte` (a další výčty typu char a třídy výčtu). Vzhledem k `std::copy` `is_trivially_copyable` tomu, že je odeslání pomocí, nepotřebuje žádné změny.
- Standardní knihovna už neobsahuje destruktory prázdných závorek, jejichž typy by měly být jenom triviální – zničitelné.

## <a name="other-libraries"></a>Jiné knihovny

### <a name="open-source-library-support"></a>Podpora open source knihovny

**Vcpkg** je open source nástroj pro příkazový řádek, který výrazně zjednodušuje proces získávání a vytváření Open Source statických knihovny a knihoven DLL C++ v aplikaci Visual Studio. Další informace najdete v tématu [vcpkg: Správce balíčků pro C++](../build/vcpkg.md).

### <a name="cpprest-sdk-290"></a>CPPRest SDK 2.9.0

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

Rozhraní Web API pro různé platformy pro C++ bylo CPPRestSDK aktualizované na verzi 2.9.0. Další informace najdete v tématu [CppRestSDK 2.9.0 je k dispozici na GitHubu](https://devblogs.microsoft.com/cppblog/cpprestsdk-2-9-0-is-available-on-github/).

### <a name="atl"></a>ATL

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- Ještě další sada oprav shody názvů – vyhledávání
- Existující konstruktory přesunutí a operátory přiřazení přesunu jsou teď správně označené jako nevyvolání.
- Zrušení potlačení platných upozornění C4640 týkajícího o bezpečné inicializaci vlákna místních statických hodnot v atlstr. h
- Inicializace lokálních statických proměnných při použití ATL k sestavení knihovny DLL byla v sadě nástrojů XP automaticky vypnuta. Nyní to není. **`/Zc:threadSafeInit-`** Pokud nechcete inicializaci bezpečnou pro přístup z více vláken, můžete přidat do nastavení projektu.

### <a name="visual-c-runtime"></a>Modul runtime Visual C++

- New header "cfguard. h" pro symboly ochrany toku řízení.

## <a name="visual-studio-2017-c-ide"></a>Visual Studio 2017 C++ IDE

- Výkon při změně konfigurace je teď vyšší u nativních projektů C++ a mnohem vyšší u projektů C++/CLI. Když se konfigurace řešení aktivuje poprvé, bude se teď zrychlit a všechny pozdější Aktivace této konfigurace řešení budou skoro okamžité.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

- Několik průvodců projektu a kódu je přepsaných ve stylu dialogu podpisu.
- **Přidat třídu** nyní spustí Průvodce přidáním třídy přímo. Všechny ostatní položky, které byly dříve tady, jsou teď dostupné v části **přidat > novou položku**.
- Projekty Win32 jsou nyní pod kategorií **Desktop systému Windows** v dialogovém okně **Nový projekt** .
- Šablony **konzolové** aplikace pro Windows a **aplikace klasické pracovní plochy** nyní vytvářejí projekty bez zobrazení průvodce. V rámci stejné kategorie je k dispozici nový **Průvodce pracovní plocha systému Windows** , ve kterém se zobrazují stejné možnosti jako původní průvodce **konzolové aplikace Win32** .

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

Několik operací C++, které používají modul IntelliSense pro refaktoring a navigaci v kódu, se spouští mnohem rychleji. Následující čísla jsou založena na řešení Visual Studio chrom s 3500 projekty:

|||
|-|-|
|Příznak|Zlepšení výkonu|
|přejmenování|5.3 x|
|Změnit signaturu |4.5 x|
|Najít všechny odkazy|4.7 x|

C++ teď podporuje kombinaci kláves Ctrl + kliknutí **Přejít k definici**, která usnadňuje navigaci myši na definice. Ve výchozím nastavení je teď součástí produktu i Vizualizér struktury ze sady Power nástrojů pro produktivitu.

## <a name="intellisense"></a>IntelliSense

- Ve výchozím nastavení je nyní používán nový databázový stroj využívající SQLite. Nový modul zrychluje databázové operace jako **Přejít k definici** a **najde všechny odkazy**. Významně zlepšuje počáteční dobu analýzy řešení. Nastavení se přesunulo do **nástrojů > možnosti > textový Editor > C/C++ > rozšířené**. (Dříve bylo pod... C/C++ > experimentální.)

- Vylepšili jsme výkon technologie IntelliSense v projektech a souborech, které nepoužívají předkompilované hlavičky – pro hlavičky aktuálního souboru se vytvoří Automatická Předkompilovaná hlavička.

- Přidali jsme do seznamu chyb filtrování a nápovědu k chybám technologie IntelliSense. Kliknutí na sloupec s chybami teď umožní je filtrovat. Kromě toho kliknutím na konkrétní chyby nebo stisknutím klávesy F1 spustíte online vyhledávání chybové zprávy.

  ![Seznam chyb](media/ErrorList1.png "Seznam chyb")

  ![Filtrovaný seznam chyb](media/ErrorList2.png "Filtrovaný seznam chyb")

- Přidali jsme možnost filtrovat položky seznamu členů podle typu.

  ![Filtrování seznamu členů](media/mlfiltering.png "Filtrování seznamu členů")

- Přidali jsme novou experimentální funkci prediktivní technologie IntelliSense, která poskytuje kontextově závislé filtrování toho, co se zobrazuje v seznamu členů. Další informace najdete v tématu [vylepšení C++ IntelliSense – prediktivní technologie intellisense & filtrování](https://devblogs.microsoft.com/cppblog/c-intellisense-improvements-predictive-intellisense-filtering/).
- **Najít všechny odkazy** (SHIFT + F12) nyní usnadňuje snadnou navigaci, a to i v komplexních základech kódu. Poskytuje pokročilé seskupení, filtrování, řazení, hledání v rámci výsledků a (u některých jazyků), takže můžete získat jasné informace o svých odkazech. V jazyce C++ nové uživatelské rozhraní obsahuje informace o tom, jestli se čte z proměnné nebo do ní zapisovat.
- Funkce změny tečky na šipku technologie IntelliSense se změnila z experimentální na pokročilou a teď je ve výchozím nastavení povolená. Funkce editoru **rozšiřují obory** a zároveň se přesunula **Priorita** z experimentální na pokročilou.
- Funkce experimentálního refaktoringu **změnit signaturu** a **extrahovat funkci** jsou teď ve výchozím nastavení dostupné.
- Bylo přidáno experimentální funkce rychlejšího načítání projektů pro projekty v jazyce C++. Při příštím otevření projektu C++ se načtou rychleji a čas po jeho načtení bude *mnohem* rychlejší.
- Některé z těchto funkcí jsou společné pro jiné jazyky a některé jsou specifické pro jazyk C++. Další informace o těchto nových funkcích naleznete v tématu [oznamujeme vydání sady Visual Studio "15" Preview 5](https://devblogs.microsoft.com/visualstudio/announcing-visual-studio-15-preview-5/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

- Byla přidána podpora pro ClangFormat. Další informace najdete v tématu [Podpora ClangFormat v aplikaci Visual Studio 2017](https://devblogs.microsoft.com/cppblog/clangformat-support-in-visual-studio-2017-15-7-preview-1/).

## <a name="non-msbuild-projects-with-open-folder"></a>Projekty jiného typu než MSBuild s otevřenou složkou

Visual Studio 2017 zavádí funkci **otevřené složky** . Umožňuje kódování, sestavení a ladění ve složce obsahující zdrojový kód bez nutnosti vytvářet žádná řešení nebo projekty. Nyní je mnohem jednodušší začít se sadou Visual Studio, a to i v případě, že projekt není projekt založený na MSBuildu. Při **otevření složky** získáte přístup k výkonným funkcím pro porozumění, úpravám, sestavování a ladění kódu. Jsou stejné jako ty, které už Visual Studio poskytují pro projekty MSBuild. Další informace naleznete v tématu [Otevřít složku projekty pro jazyk C++](../build/open-folder-projects-cpp.md).

- Vylepšení prostředí Otevřít složku Můžete přizpůsobit prostředí pomocí těchto souborů. JSON:
  - CppProperties.json použijte k přizpůsobení technologie IntelliSense a prostředí procházení.
  - Tasks.json použijte k přizpůsobení kroků sestavení.
  - Launch.json použijte k přizpůsobení prostředí ladění.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

- Vylepšená podpora alternativních kompilátorů a prostředí pro sestavování, jako jsou MinGW a Cygwin. Další informace najdete v tématu [použití MinGW a Cygwin s Visual C++ a otevření složky](https://devblogs.microsoft.com/cppblog/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/).
- Přidání podpory pro definování globálních a specifických proměnných prostředí specifických pro konfiguraci v CppProperties. JSON a CMakeSettings. JSON. Tyto proměnné prostředí lze spotřebovat pomocí konfigurací ladění definovaných v příkazu Launch. vs. JSON a úkoly v Tasks. vs. JSON. Další informace najdete v tématu [přizpůsobení prostředí pomocí Visual C++ a otevřené složky](https://devblogs.microsoft.com/cppblog/customizing-your-environment-with-visual-c-and-open-folder/).
- Vylepšená podpora generátoru expertem CMake, včetně možnosti snadno cílit na 64 bitů na platformě.

## <a name="cmake-support-via-open-folder"></a>Podpora CMake prostřednictvím otevřené složky

Sada Visual Studio 2017 zavádí podporu pro použití projektů CMake bez převodu na soubory projektu MSBuild (. vcxproj). Další informace najdete v tématu [projekty cmake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md). Otevření projektů CMake s **otevřenou složkou** automaticky nakonfiguruje prostředí pro úpravy, sestavování a ladění C++.

- C++ IntelliSense funguje bez nutnosti vytvořit soubor CppProperties. JSON v kořenové složce. Přidali jsme také nové rozevírací seznam umožňující uživatelům snadno přepínat mezi konfiguracemi poskytovanými soubory CMake a CppProperties. JSON.

- Prostřednictvím souboru CMakeSettings.json, který je umístěný ve stejné složce jako soubor CMakeLists.txt, se podporuje další konfigurace.

  ![Otevřená složka CMake](media/cmake-cpp.png "Otevřená složka CMake")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

- Přidala se podpora pro generátor expertem CMake.

##### <a name="visual-studio-2017-version-154"></a>Visual Studio 2017 verze 15.4

- Byla přidána podpora pro import existujících mezipamětí CMake.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- Přidala se podpora pro CMake 3,11, analýza kódu v projektech CMake, zobrazení cílů v Průzkumník řešení, možnosti generování mezipaměti a kompilace jednoho souboru. Další informace najdete v tématu [Podpora cmake v sadě Visual Studio](https://devblogs.microsoft.com/cppblog/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) a [projektech cmake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md).

## <a name="windows-desktop-development"></a>Vývoj desktopových aplikací pro Windows

Při instalaci původní úlohy pro C++ teď poskytujeme podrobnější prostředí instalace. Přidali jsme volitelné součásti, které vám umožní vybrat a nainstalovat jen ty nástroje, které potřebujete. Uvedené velikosti instalace pro součásti uvedené v uživatelském rozhraní instalačního programu jsou nesprávné a podceňují skutečnou celkovou velikost.

Když chcete úspěšně vytvářet projekty Win32 v úloze vývoje desktopových aplikací v C++, musíte nainstalovat sadu nástrojů i sadu Windows SDK. Nainstalujte doporučené (vybrané) komponenty **VC + + 2017 v141 sady nástrojů (x86, x64)** a **Windows 10 SDK (10.0. NNNNN)** , abyste se ujistili, že funguje. Pokud nejsou potřebné nástroje nainstalované, projekty se nevytvoří úspěšně a průvodce se zablokuje.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

Nástroje pro Visual C++ Build (dříve dostupné jako samostatný produkt) jsou teď zahrnuté jako úlohy v Instalační program pro Visual Studio. Tato úloha nainstaluje pouze nástroje potřebné pro sestavení projektů C++ bez instalace prostředí IDE sady Visual Studio. Zahrnují se sady nástrojů v140 i v141. Sada nástrojů v141 obsahuje nejnovější vylepšení sady Visual Studio 2017 verze 15,5. Další informace najdete v tématu [Visual Studio Build Tools nyní zahrnují sady nástrojů MSVC a VS2015](https://devblogs.microsoft.com/cppblog/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/).

## <a name="linux-development-with-c"></a>Vývoj linuxových aplikací v jazyce C++

Oblíbené rozšíření [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) je teď součástí sady Visual Studio. Tato instalace nabízí všechno, co potřebujete k vývoji a ladění aplikací v jazyce C++, které se spouštějí v prostředí systému Linux.

##### <a name="visual-studio-2017-version-152"></a>Visual Studio 2017 verze 15.2

Vylepšení byla provedená ve sdílení kódu mezi platformami a vizualizací typů. Další informace najdete v tématu [vylepšení pro Linux C++ pro sdílení kódu pro různé platformy a vizualizaci typů](https://devblogs.microsoft.com/cppblog/linux-cross-platform-and-type-visualization/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- Úloha Linux přidala podporu pro **rsync** jako alternativu k protokolu **SFTP** pro synchronizaci souborů na vzdálených počítačích se systémem Linux.
- Je přidána podpora pro různé kompilace cílící na mikrokontroléry ARM. Pokud ho chcete v instalaci povolit, zvolte **vývoj pro Linux s** využitím úlohy C++ a vyberte možnost pro **integrovaný vývoj a vývoj IoT**. Tato možnost přidá nástroje pro více kompilačních nástrojů ARM RSZ a provede instalaci. Další informace najdete v tématu o [příčné kompilaci ARM RSZ v sadě Visual Studio](https://devblogs.microsoft.com/cppblog/arm-gcc-cross-compilation-in-visual-studio/).
- Přidala se podpora pro CMake. Teď můžete pracovat na svém stávajícím základu kódu CMake, aniž byste ho museli převádět na projekt sady Visual Studio. Další informace najdete v tématu [konfigurace projektu Linux cmake](../linux/cmake-linux-project.md).
- Byla přidána podpora pro spouštění vzdálených úloh. Tato funkce umožňuje spustit libovolný příkaz ve vzdáleném systému, který je definován ve Správci připojení sady Visual Studio. Vzdálené úlohy také poskytují možnost kopírování souborů do vzdáleného systému.
Další informace najdete v tématu [konfigurace projektu Linux cmake](../linux/cmake-linux-project.md).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

- Různá vylepšení scénářů pro úlohy Linux. Další informace najdete v tématu [vylepšení úlohy Linux C++ do systému projektu, okna konzoly Linux, rsync a připojení k procesu](https://devblogs.microsoft.com/cppblog/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/).
- Technologie IntelliSense pro záhlaví na vzdálených připojeních systému Linux. Další informace najdete v tématech [technologie IntelliSense pro vzdálené systémy Linux](https://devblogs.microsoft.com/cppblog/intellisense-for-remote-linux-headers/) a [konfigurace projektu pro Linux cmake](../linux/cmake-linux-project.md).

## <a name="game-development-with-c"></a>Vývoj her v jazyce C++

Využijte naplno potenciál C++ k vytváření profesionálních her využívajících technologii DirectX nebo Cocos2d.

## <a name="mobile-development-with-c-for-android-and-ios"></a>Vývoj pro mobilní zařízení pomocí C++ pro Android a iOS

Mobilní aplikace teď můžete vytvářet a ladit pomocí sady Visual Studio, která se umí zaměřit i na Android a iOS.

## <a name="universal-windows-apps"></a>Univerzální aplikace pro Windows

C++ je volitelnou součástí úlohy Universal Windows App. V současné době je nutné upgradovat projekty C++ ručně. V aplikaci Visual Studio 2017 můžete otevřít projekt Univerzální platforma Windows cílené na v140. Pokud však nemáte nainstalovanou sadu Visual Studio 2015, je nutné vybrat sadu nástrojů v141 Platform na stránkách vlastností projektu.

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>Nové možnosti pro C++ na Univerzální platforma Windows (UWP)

Nyní máte nové možnosti pro psaní a balení aplikací C++ pro Univerzální platforma Windows a Windows Store: infrastruktura pro stolní počítače umožňuje zabalit stávající desktopovou aplikaci nebo objekt COM k nasazení prostřednictvím Windows Storu. Nebo můžete pro nasazení prostřednictvím svých stávajících kanálů prostřednictvím načítacího načítání. Nové funkce systému Windows 10 umožňují přidat do aplikace klasické pracovní plochy funkce UWP různými způsoby. Další informace najdete v tématu [most pro stolní počítače](/windows/uwp/porting/desktop-to-uwp-root).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

Je přidána šablona projektu pro **balení aplikace systému Windows** , která významně zjednodušuje balení desktopových aplikací s využitím stolního mostu. Je k dispozici v **souboru | Nové | Projekt | Nainstalováno | Visual C++ | Univerzální platforma Windows**. Další informace najdete v tématu [sbalení aplikace pomocí sady Visual Studio (most pro stolní počítače)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

Při psaní nového kódu teď můžete použít C++/WinRT, což je standardní projekce jazyka C++ pro prostředí Windows Runtime implementované výhradně v hlavičkových souborech. Umožňuje využívání a vytváření prostředí Windows Runtime rozhraní API pomocí všech kompilátorů C++ odpovídajících standardům. C++/WinRT je navržený tak, aby poskytoval vývojářům v jazyce C++ přístup k modernímu rozhraní API pro Windows pomocí prvotřídního přístupu. Další informace najdete v tématu [c++/WinRT: moderní c++ pro prostředí Windows Runtime](https://moderncpp.com/).

Od verze Build 17025 Windows SDK Insider Preview je/WinRT C++ zahrnutý v Windows SDK. Další informace najdete v části [C++/WinRT je teď součástí Windows SDK](https://devblogs.microsoft.com/cppblog/cppwinrt-is-now-included-the-windows-sdk/).

## <a name="the-clangc2-platform-toolset"></a>Sada nástrojů platformy Clang/C2

Sada nástrojů Clang/C2, která je dodávána se sadou Visual Studio 2017, teď podporuje **`/bigobj`** přepínač, který je rozhodující pro sestavování rozsáhlých projektů. Zahrnuje také několik důležitých oprav chyb, jak ve front-endu kompilátoru, tak i v back-endu.

## <a name="c-code-analysis"></a>Analýza kódu C++

Se sadou Visual Studio se nyní distribuují moduly pro kontrolu jádra C++, které vynucují [pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines). Povolte kontrolu na stránce vlastností pro **analýzu kódu** na stránkách vlastností projektu. Rozšíření jsou pak součástí při spuštění nástroje Code Analysis. Další informace najdete v tématu [použití kontrol C++ Core Guidelines](/cpp/code-quality/using-the-cpp-core-guidelines-checkers).

![CppCoreCheck](media/CppCoreCheck.png "Stránka vlastností CppCoreCheck")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

- Byla přidána podpora pro pravidla související se správou prostředků.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- Nové C++ Core Guidelines kontroluje správnost inteligentního ukazatele, správné použití globálních inicializátorů a označení použití konstrukcí jako `goto` a špatného přetypování.

- Některá čísla upozornění, která najdete v 15.3, už nejsou k dispozici v 15.5. Tato upozornění byla nahrazena specifičtějšími kontrolami.

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 verze 15.6

- Přidání podpory pro analýzu jednoho souboru a vylepšení výkonu analýzy za běhu. Další informace naleznete v tématu [vylepšení statické analýzy C++ pro Visual Studio 2017 15,6 Preview 2](https://devblogs.microsoft.com/cppblog/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/)

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

- Byla přidána podpora pro [/analyze: RuleSet](../build/reference/analyze-code-analysis.md), která umožňuje určit pravidla analýzy kódu, která se mají spustit.
- Přidala se podpora pro další pravidla C++ Core Guidelines.  Další informace najdete v tématu [použití kontrol C++ Core Guidelines](/cpp/code-quality/using-the-cpp-core-guidelines-checkers).

## <a name="unit-testing-in-visual-studio-2017"></a>Testování částí v aplikaci Visual Studio 2017

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

Google Test adaptér a zesílení. adaptér testu je nyní k dispozici jako součást **vývoje plochy pomocí úlohy C++** . Jsou integrovány do **Průzkumníka testů**. Pro projekty CMake (pomocí otevřené složky) se přidá podpora CTest, i když plná integrace s **průzkumníkem testů** ještě není dostupná. Další informace naleznete v tématu [zápis testů jednotek pro C/C++](/visualstudio/test/writing-unit-tests-for-c-cpp).

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 verze 15.6

- Byla přidána podpora `Boost.Test` dynamické knihovny.
- `Boost.Test`Šablona položky je nyní dostupná v integrovaném vývojovém prostředí.

Další informace naleznete v tématu [ `Boost.Test` testování částí: podpora dynamické knihovny a nová šablona položky](https://devblogs.microsoft.com/cppblog/boost-test-unit-testing-dynamic-library-support-and-new-item-template/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

Byla přidána podpora [CodeLens](/visualstudio/ide/find-code-changes-and-other-history-with-codelens) pro projekty testování částí C++. Další informace najdete v tématu [oznámení CodeLens pro testování částí C++](https://devblogs.microsoft.com/cppblog/announcing-codelens-for-c-unit-testing/).

## <a name="visual-studio-graphics-diagnostics"></a>Diagnostika grafiky sady Visual Studio

Nástroje pro Diagnostika grafiky sady Visual Studio: můžete je použít k zaznamenávání a analýze problémů s výkonem a výkonu v aplikacích Direct3D. Používejte je v aplikacích, které se spouští místně na počítači s Windows, v emulátoru zařízení s Windows nebo na vzdáleném počítači nebo zařízení.

- **Vstupní & výstup pro shadery vrcholů a geometrie:** Možnost zobrazit vstup a výstup funkcí vertex shader a geometrie shaderu byla jednou z nejvíce požadovaných funkcí. Teď se podporuje v nástrojích. Kliknutím na fázi VS nebo GS v zobrazení fáze zřetězení spustíte kontrolu jeho vstupu a výstupu v následující tabulce.

  ![Vstup/výstup pro shadery](media/io-shaders.png)

- **Hledání a filtrování v tabulce objektů:** Poskytuje rychlý a snadný způsob, jak najít prostředky, které hledáte.

  ![Search](media/search.png)

- **Historie prostředků:** Toto nové zobrazení nabízí zjednodušený způsob, jak zobrazit celou historii změn prostředku, jak bylo použito při vykreslování zachyceného snímku. Pokud chcete vyvolat historii pro libovolný prostředek, klikněte na ikonu hodiny vedle libovolného hypertextového odkazu prostředku.

  ![Historie prostředků](media/resource-history.png)

  Zobrazí se okno Nový nástroj **historie prostředků** , které se vyplní historií změn prostředku.

  ![Změna historie prostředků](media/resource-history-change.png)

  Můžete zachytit snímky s povoleným zachytáváním zásobníku volání. Umožňuje rychle odvodit kontext každé události změny a zkontrolovat ji v rámci projektu sady Visual Studio. Možnost úplného zachycení zásobníku nastavte v dialogovém okně Visual Studio **Tools > Options** v části **Diagnostika grafiky**.

- **Statistika rozhraní API:** Podívejte se na Přehled využití rozhraní API ve vašem snímku na nejvyšší úrovni. Je to užitečné pro zjišťování volání, která nemůžete dělat vůbec, nebo volání, která provádíte příliš často. Toto okno je k dispozici prostřednictvím **zobrazení > statistiky rozhraní API** v analyzátor grafiky sady Visual Studio.

  ![Statistika rozhraní API](media/api-stats.png)

- **Statistika paměti:** Zobrazit, kolik paměti ovladač přiděluje pro prostředky, které vytvoříte v rámci tohoto rámce. Toto okno je k dispozici prostřednictvím **zobrazení > statistiky paměti** v **analyzátor grafiky sady Visual Studio**. Chcete-li zkopírovat data do souboru CSV pro zobrazení v tabulce, klikněte pravým tlačítkem myši a vyberte možnost **Kopírovat vše**.

  ![Statistiky paměti](media/memory-stats.png)

- **Ověření snímku:** Seznam nových chyb a upozornění nabízí snadný způsob, jak procházet seznam událostí na základě potenciálních problémů zjištěných ladicí vrstvou Direct3D. Kliknutím na **zobrazit > ověření rámce** v analyzátor grafiky sady Visual Studio otevřete okno. Pak kliknutím na **Spustit ověření** spusťte analýzu. Dokončení může trvat několik minut, v závislosti na složitosti snímku.

  ![Ověření snímku](media/frame-validation.png)

- **Analýza snímků pro D3D12:** Pomocí analýzy snímků můžete analyzovat výkon volání při volání s použitím pořízených experimentů "Co je if". Přepněte na kartu analýza snímků a spusťte analýzu pro zobrazení sestavy. Další podrobnosti najdete na [GoingNative 25: Visual Studio Analýza grafických snímků](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) video.

  ![Analýza snímků](media/frame-analysis.png)

- **Vylepšení využití GPU:** Pomocí nástroje Profiler využití GPU sady Visual Studio můžete otevřít trasování pomocí zobrazení GPU nebo nástroje Windows Performance Analyzer (WPA), kde najdete podrobnější analýzu. Pokud máte sadu Windows Performance Toolkit nainstalovanou, existují dva hypertextové odkazy: jeden pro WPA a druhý pro zobrazení GPU, v pravém dolním rohu Přehled relace.

  ![Využití GPU](media/gpu-usage.png)

  Trasování, která jste otevřeli v zobrazení GPU prostřednictvím tohoto odkazu, se synchronizují a přiblíží se k přiblížení a posouvání časové osy zobrazení GPU. Zaškrtávací políčko v VS Určuje, jestli je synchronizace povolená nebo ne.

  ![Zobrazení GPU](media/gpu-view.png)

::: moniker-end

::: moniker range="=vs-2015"

Úplný seznam toho, co je nového v rámci sady Visual Studio 2015 Update 3, najdete v článku [Visual C++ novinky 2003 až 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

Další informace o tom, co je nového ve všech verzích sady Visual Studio 2015, najdete v poznámkách k verzi. Jsou propojeny z [historie zpráv k vydání verze sady Visual Studio 2015](/visualstudio/releasenotes/vs2015-version-history).

Informace o novinkách jazyka C++ v aplikaci Visual Studio 2019 naleznete v tématu [co je nového pro jazyk c++ v aplikaci Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019).

Informace o novinkách jazyka C++ v aplikaci Visual Studio 2017 naleznete v tématu [co je nového pro jazyk c++ v aplikaci Visual studio 2017](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017).

::: moniker-end
