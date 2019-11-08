---
title: Novinky v jazyce C++ v sadě Visual Studio
ms.date: 07/02/2019
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: bde8b8e17c3186d22493f099a5f7d1b5a2646a67
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754131"
---
# <a name="whats-new-for-c-in-visual-studio"></a>Novinky v jazyce C++ v sadě Visual Studio

::: moniker range=">=vs-2019"

Visual Studio 2019 přináší mnoho aktualizací a oprav prostředí Microsoftu C++ . Opravili jsme spoustu chyb a problémů v kompilátoru a nástrojích. Mnohé z těchto problémů byly odeslány zákazníky prostřednictvím [nahlášení problému](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019) a [poskytují návrh](https://developercommunity.visualstudio.com/spaces/62/index.html) možností v části **Odeslat názor**. Děkujeme vám, že hlásíte chyby! Další informace o tom, co je nového ve všech verzích sady Visual Studio, najdete v části [novinky v aplikaci Visual studio 2019](/visualstudio/ide/whats-new-visual-studio-2019). Informace o tom, co je nového C++ v aplikaci visual Studio 2017, najdete v tématu [novinky C++ v aplikaci Visual Studio 2017](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017). Informace o tom, co je nového C++ v aplikaci Visual Studio 2015 a dřívějších verzích, najdete v článku [ C++ co je nového 2003 až 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="c-compiler"></a>kompilátor C++

- Vylepšená podpora pro funkce C++ 17 a opravy oprav a experimentální Podpora funkcí C++ 20, jako jsou moduly a korutiny. Podrobné informace naleznete v tématu [ C++ vylepšení shody v aplikaci Visual Studio 2019](cpp-conformance-improvements.md).

- Možnost `/std:c++latest` nyní obsahuje funkce C++ 20, které nejsou nutně kompletní, včetně počáteční podpory pro operátor C++ 20 \<= > ("prostorové") pro trojrozměrné porovnání.

- Přepínač C++ kompilátoru `/Gm` je nyní zastaralý. Pokud je explicitně definován, je vhodné zakázat přepínač `/Gm` ve skriptech sestavení. Můžete ale také bezpečně ignorovat upozornění na vyřazení z `/Gm`, protože při použití příkazu "zpracovávat upozornění jako chyby" (`/WX`) se nepovažuje za chybu.

- Protože MSVC zahájí implementaci funkcí z konceptu standardu C++ 20 pod příznakem `/std:c++latest`, `/std:c++latest` je nyní nekompatibilní s `/clr` (všechny charaktery), `/ZW`a `/Gm`. V aplikaci Visual Studio 2019 použijte `/std:c++17` nebo `/std:c++14` režimy při kompilování s `/clr`, `/ZW`nebo `/Gm` (ale viz předchozí odrážka).

- U aplikací C++ pro konzoly a klasickou pracovní plochu se už negenerují předkompilované hlavičky.

### <a name="codegen-security-diagnostics-and-versioning"></a>CodeGen, zabezpečení, diagnostika a správa verzí

Vylepšená analýza pomocí `/Qspectre` pro zajištění pomoci zmírnění Spectre varianty 1 (CVE-2017-5753). Další informace najdete v tématu [zmírnění hrozeb Spectre v MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).

## <a name="c-standard-library-improvements"></a>C++vylepšení standardní knihovny

- Implementace dalších funkcí knihovny C++ 17 a C++ 20 a oprav správnosti. Podrobné informace naleznete v tématu [ C++ vylepšení shody v aplikaci Visual Studio 2019](cpp-conformance-improvements.md).

- Clang-formát se pro lepší čitelnosti C++ používá v hlavičkách standardních knihoven.

- Vzhledem k tomu, že Visual Studio C++teď podporuje pouze můj kód pro, standardní knihovna už nepotřebuje k tomu, aby k dosažení stejného efektu poskytovala vlastní strojní zařízení `std::function` a `std::visit`. Odebrání tohoto strojového zařízení do značné míry nemá žádné efekty viditelné uživatelem. Jedinou výjimkou je, že kompilátor již nebude vydávat diagnostiku, která indikuje problémy na řádku 15732480 nebo 16707566 \<type_traits > nebo \<variant >.

## <a name="performancethroughput-improvements-in-the-compiler-and-standard-library"></a>Vylepšení výkonu a propustnosti v kompilátoru a standardní knihovně

- Vylepšení propustnosti sestavení, včetně způsobu, jakým linker zpracovává vstupně-výstupní operace se soubory, a čas propojení v typu PDB sloučení a vytváření.

- Byla přidána základní podpora pro vektory OpenMP SIMD. Můžete ji povolit pomocí nového přepínače kompilátoru `-openmp:experimental`. Tato možnost umožňuje, aby byly smyčky s poznámkou `#pragma omp simd` potenciálně vektorované. Není zaručeno vektorování a poznámky, které jsou opatřeny poznámkami, ale nebudou vektory, zobrazily upozornění. Nepodporují se žádné klauzule SIMD. jsou ignorovány a je hlášeno upozornění.

- Byl přidán nový přepínač příkazového řádku `-Ob3`, což je účinnější verze `-Ob2`. `-O2` (optimalizace binárního souboru pro rychlost) stále implikuje `-Ob2` ve výchozím nastavení. Pokud zjistíte, že kompilátor není dostatečně vložený, zvažte předání `-O2 -Ob3`.

- Pro podporu rozvektoru smyček pomocí volání funkcí matematické knihovny a určitých dalších operací, jako je celočíselné dělení, jsme přidali podporu pro vnitřní funkce krátké knihovny Math Vector (SVML). Tyto funkce počítají hodnoty ekvivalentu bitového vektoru 128-bit, 256 nebo 512. Definice podporovaných funkcí najdete v příručce [Intel Intrinsic Guide](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML).

- Nové a vylepšené optimalizace:

  - Konstantní skládání a aritmetické zjednodušení pro výrazy pomocí vnitřních vektorů SIMD pro formuláře typu float i Integer.

  - Výkonnější analýza pro extrakci informací z toku řízení (příkazy if/else/Switch) pro odebrání větví vždy ověřena jako true nebo false.

  - Vylepšené rozmemsetování pro použití instrukcí SSE2 Vector

  - Vylepšené odebrání nezbytečných kopií struktury nebo tříd, C++ zejména pro programy, které přecházejí hodnotou.

  - Vylepšená optimalizace kódu pomocí `memmove`, jako je například `std::copy` nebo `std::vector` a konstrukce `std::string`.

- Optimalizuje se standardní fyzický návrh knihovny, aby se předešlo kompilování částí standardní knihovny, která není přímo zahrnutá. Tato změna vyjme čas sestavení prázdného souboru, který obsahuje pouze \<vektor > na polovinu. V důsledku toho možná budete muset přidat direktivy `#include` pro hlavičky, které byly dříve nepřímo zahrnuté. Například kód, který používá `std::out_of_range` může nyní potřebovat přidat `#include <stdexcept>`. Kód, který používá operátor vložení datového proudu, teď může být potřeba přidat `#include <ostream>`. Výhodou je, že pouze jednotky překladu ve skutečnosti používají \<stdexcept > nebo \<ostream > komponenty platíte náklady na propustnost při jejich kompilaci.

- `if constexpr` bylo použito ve více umístěních ve standardní knihovně pro lepší propustnost a menší velikost kódu v operacích kopírování, v permutacích, jako je reverzní a otočení a v knihovně paralelních algoritmů.

- Standardní knihovna nyní interně používá `if constexpr` k omezení doby kompilace, a to i v režimu C++ 14.

- Detekce dynamického propojování modulu runtime pro knihovnu paralelních algoritmů již nepoužívá celou stránku k uložení pole s ukazatelem na funkci. Označení této paměti jen pro čtení bylo považováno za již nerelevantní z hlediska zabezpečení.

- konstruktor `std::thread`již nečeká na spuštění vlákna a již nebude vkládat tolik vrstev volání funkce mezi podkladovou knihovnou C `_beginthreadex` a zadaným objektem, který lze volat. Dřív `std::thread` vložit 6 funkcí mezi `_beginthreadex` a předaným objektem, který je k dispozici, se snížil jenom na 3 (2, které jsou jenom `std::invoke`). Tato změna také vyřeší chybu překrytí časování, kde `std::thread` konstruktor přestane reagovat, pokud se systémové hodiny změnily přesně v okamžiku, kdy se vytvořila `std::thread`.

- Opravili jsme při implementaci `std::hash<std::filesystem::path>`regresi výkonu `std::hash`.

- Standardní knihovna nyní používá destruktory namísto bloků catch na několika místech pro dosažení správnosti. Tato změna vede k lepší interakci ladicího programu: výjimky, které jste vyvolali pomocí standardní knihovny v příslušných umístěních, se nyní zobrazují jako vyvolané z původní lokality throw, nikoli z našeho opětovného vyvolání. Nebyly eliminovány všechny bloky catch standardní knihovny. Očekáváme, že počet bloků catch bude v pozdějších verzích MSVC snížen.

- Neoptimální CodeGen v `std::bitset` způsobený podmíněnou operací throw uvnitř funkce s výjimkou byla opravena vynásobením této aktivační cesty.

- `std::list` a `std::unordered_*` rodina používají iterátory bez ladění interně na více místech.

- Několik `std::list` členů bylo změněno tak, aby opakovaně používalo seznam uzlů tam, kde je to možné, spíše než zrušení přidělení a jejich přidělení. Například s ohledem na `list<int>`, která již má velikost 3, volání `assign(4, 1729)` nyní přepíše čísla v prvních 3 uzlech seznamu a přidělí jeden nový uzel seznamu s hodnotou 1729.

- Všechna volání knihovny Standard `erase(begin(), end())` byla změněna na `clear()`.

- `std::vector` teď v určitých případech Inicializuje a maže prvky efektivněji.

- Vylepšení `std::variant`, aby bylo lépe optimalizované pro optimalizaci, což vede k lepšímu vygenerování kódu. Vkládání kódu je teď mnohem lepší díky `std::visit`.

## <a name="c-ide"></a>C++ IDE

### <a name="live-share-c-support"></a>Podpora C++ Live Share

[Live Share](/visualstudio/liveshare/) teď podporuje C++, což vývojářům umožňuje využívat Visual Studio nebo Visual Studio Code spolupracovat v reálném čase. Další informace najdete v tématu [oznámení Live Share pro C++: sdílení v reálném čase a spolupráci.](https://devblogs.microsoft.com/cppblog/cppliveshare/)

### <a name="intellicode-for-c"></a>IntelliCode proC++

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 verze 16,1

IntelliCode je volitelné rozšíření, které používá vlastní rozsáhlé školení a váš kontext kódu k umístění toho, co je nejpravděpodobnější v horní části seznamu dokončení. Je často možné eliminovat nutnost procházení seznamu. Pro C++nástroj IntelliCode nabízí největší nápovědu při používání oblíbených knihoven, jako je například standardní knihovna. Je k dispozici v instalačním programu jako komponenta úlohy. Další informace najdete v tématu [návrhy dokončování kódu s asistencí AI do C++ IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/).

### <a name="template-intellisense"></a>IntelliSense šablony

**Panel šablon** nyní používá uživatelské rozhraní **náhledu** místo modálního okna, podporuje vnořené šablony a předem naplní všechny výchozí argumenty do **náhledu okna**. Další informace najdete v tématu [vylepšení šablon IntelliSense pro Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/template-intellisense-improvements-for-visual-studio-2019-preview-2/). Rozevírací seznam **naposledy použitých** na **panelu šablon** vám umožní rychle přepínat mezi předchozími sadami vzorových argumentů.

### <a name="new-start-window-experience"></a>Nové prostředí Start okna

Při spuštění rozhraní IDE se zobrazí nové okno Start s možnostmi pro otevření posledních projektů, klonování kódu ze správy zdrojového kódu, otevření místního kódu jako řešení nebo složky nebo vytvoření nového projektu. Dialogové okno Nový projekt se také převedlo na funkce hledání, které by bylo možné filtrovat.

### <a name="new-names-for-some-project-templates"></a>Nové názvy pro některé šablony projektů

Změnili jsme několik názvů šablon projektů a popisy tak, aby se vešly do dialogového okna aktualizovaný nový projekt.

### <a name="various-productivity-improvements"></a>Různá vylepšení produktivity

Visual Studio 2019 obsahuje následující funkce, které vám pomůžou usnadnit a intuitivnější kódování:

- Rychlé opravy pro:
  - Přidat chybějící #include
  - NULL na nullptr
  - Přidat chybějící středník
  - Vyřešit chybějící obor názvů nebo obor
  - Nahradit chybné operandy indirekce (\* & a & na \*)
- Rychlé informace o bloku najetím myší na pravou složenou závorku
- Náhled souboru hlaviček nebo kódu
- Přejít k definici při #include otevře soubor

Další informace najdete v tématu [ C++ vylepšení produktivity v aplikaci Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/c-productivity-improvements-in-visual-studio-2019-preview-2/).

### <a name="quickinfo-improvements"></a>Vylepšení QuickInfo

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 verze 16,1

Rychlé informace nyní dodržuje sémantickou zabarvení editoru. Má také nový odkaz **Search online** , který vyhledá online dokumenty, kde najdete další informace o konstrukci kódu na pojetí. U kódu v červeném vlnovce vám odkaz, který poskytuje rychlé informace, vyhledá chybu online. Tímto způsobem není nutné znovu zadávat zprávu do prohlížeče. Další informace naleznete v tématu [rychlá vylepšení informací v aplikaci Visual Studio 2019: zabarvení a hledání online](https://devblogs.microsoft.com/cppblog/quick-info-improvements-in-visual-studio-2019-colorization-and-search-online/).

### <a name="intellicode-available-in-c-workload"></a>IntelliCode dostupné v C++ zatížení

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 verze 16,1

IntelliCode **se C++**  teď dodává jako volitelná komponenta pro vývoj desktopových aplikací. Další informace najdete v tématu [ C++ Vylepšená IntelliCode nyní dodávána se sadou Visual Studio 2019](https://devblogs.microsoft.com/cppblog/improved-c-intellicode-now-ships-with-visual-studio-2019/).

## <a name="cmake-support"></a>Podpora CMake

- Podpora CMake 3,14

- Sada Visual Studio nyní může otevřít existující mezipaměti CMake generované externími nástroji, jako je CMakeGUI, přizpůsobené systémy meta-buildu nebo skripty sestavení, které spouštějí cmake. exe samotné.

- Vylepšený výkon technologie IntelliSense.

- Nový editor nastavení poskytuje alternativu k ruční úpravě souboru CMakeSettings. JSON a poskytuje určitou paritu s CMakeGUI.

- Visual Studio vám pomůže rozběhnout vývoj v jazyce C++ s nástroji CMake na Linuxu díky rozpoznání, jestli máte na počítači s Linuxem kompatibilní verzi CMake. Pokud ne, aplikace vám nabídne její instalaci.

- Nekompatibilní nastavení v CMakeSettings, jako jsou neshodné architektury nebo nekompatibilní nastavení generátoru CMake, zobrazují v editoru JSON vlnové hodnoty a chyby v seznamu chyb.

- Po spuštění příkazu `vcpkg integrate install` se automaticky rozpozná sada nástrojů vcpkg a povolí se pro projekty CMake, které jsou otevřené v integrovaném vývojovém prostředí. Toto chování můžete vypnout tak, že v nástroji CMakeSettings zadáte prázdný soubor sady nástrojů.

- Projekty CMake teď ve výchozím nastavení aktivují ladění s možností Pouze můj kód.

- Upozornění statické analýzy u projektů CMake teď můžete zpracovat na pozadí a zobrazit v editoru.

- Vymažte sestavení a nakonfigurujte zprávy Begin a end pro projekty CMake a podporu uživatelského rozhraní pro průběh sestavení sady Visual Studio. Kromě toho je teď nastavení podrobností CMake v **nabídce nástroje > možnosti** přizpůsobení úrovně podrobností pro zprávy o sestavení a konfiguraci cmake v okno výstup.

- Nastavení `cmakeToolchain` se teď v CMakeSettings. JSON podporuje, pokud chcete zadat sady nástrojů, aniž byste museli ručně upravovat příkazový řádek CMake.

- Novou zkratku nabídky **sestavit vše** **CTRL + SHIFT + B**.

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 verze 16,1

- Integrovaná podpora pro úpravy, sestavování a ladění projektů CMake s využitím Clang/LLVM. Další informace naleznete v tématu [Podpora Clang/LLVM v aplikaci Visual Studio](https://devblogs.microsoft.com/cppblog/clang-llvm-support-in-visual-studio/).

## <a name="linux-and-the-windows-subsystem-for-linux"></a>Linux a subsystém Windows pro Linux

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 verze 16,1

- Podpora [AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) v projektech pro Linux a cmake v různých platformách. Další informace najdete v tématu [AddressSanitizer (ASan) pro úlohu Linux v aplikaci Visual Studio 2019](https://devblogs.microsoft.com/cppblog/addresssanitizer-asan-for-the-linux-workload-in-visual-studio-2019/).

- Integrovaná podpora sady Visual Studio pro C++ použití s podsystémem Windows pro Linux (WSL). Další informace najdete v tématu [ C++ se sadou Visual Studio 2019 a s podsystémem Windows pro Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

## <a name="incredibuild-integration"></a>Integrace IncrediBuild

IncrediBuild je jako volitelná součást  **C++ vývoje desktopových** aplikací. Monitor sestavení IncrediBuild je plně integrovaný v integrovaném vývojovém prostředí sady Visual Studio. Další informace naleznete v tématu [vizualizace sestavení pomocí monitoru sestavení IncrediBuild a sady Visual Studio 2019](https://devblogs.microsoft.com/cppblog/visualize-your-build-with-incredibuilds-build-monitor-and-visual-studio-2019/).

## <a name="debugging"></a>Ladění

- Pro C++ aplikace běžící ve Windows se nyní soubory PDB načítají v samostatném 64 procesu. Tato změna řeší rozsah havárií způsobený ladicím programem, který při ladění aplikací, které obsahují velký počet modulů a souborů PDB, nemá dostatek paměti.

- Hledání je povolené v oknech **kukátko**, **Automatické**hodnoty a **místní** hodnoty.

## <a name="windows-desktop-development-with-c"></a>Vývoj desktopových aplikací pro Windows pomocíC++

- Tito C++ průvodci ATL/MFC již nejsou k dispozici:

  - Průvodce komponentami ATL COM+ 1.0
  - Průvodce komponentami ATL Active Server Pages
  - Průvodce poskytovatelem OLE DB ATL
  - Průvodce stránkou vlastností ATL
  - Průvodce příjemcem OLE DB ATL
  - Příjemce knihovny MFC rozhraní ODBC
  - Třída MFC z ovládacího prvku ActiveX
  - Třída MFC z knihovny typů.

  Vzorový kód pro tyto technologie je archivován na Microsoft Docs a úložišti GitHubu VCSamples.

- V instalačním programu sady Visual Studio už není dostupná sada Windows 8.1 SDK. Doporučujeme upgradovat C++ projekty na nejnovější sadu Windows 10 SDK. Pokud máte zavedenou závislost na 8,1, můžete ji stáhnout z Windows SDK archivu.

- V nejnovější sadě nástrojů C++ už nebude k dispozici cílení na Windows XP. Cílení na XP s & kompilátory MSVC kompilátoru VS 2017 se pořád podporuje a dají se nainstalovat prostřednictvím "jednotlivých komponent".

- Naše dokumentace aktivně odrazuje od používání slučovacích modulů k nasazení modulu Runtime Visual C++. V tomto dodatečném kroku vybereme tento produkt, který označuje naše MSMs jako zastaralé. Zvažte migraci centrálního nasazení VCRuntime z balíčků MSM na balíček opětovné distribuce.

## <a name="mobile-development-with-c-android-and-ios"></a>Vývoj pro C++ mobilní zařízení (Android a iOS)

Výchozím prostředím C++ Android je nyní Android SDK 25 a Android NDK 16b.

## <a name="clangc2-platform-toolset"></a>Sada nástrojů platformy Clang/C2

Experimentální součást Clang/C2 se odebrala. Použijte sadu nástrojů MSVC pro úplný C++ soulad s normami s `/permissive-` a `/std:c++17`nebo CLANG/LLVM sada nástrojů pro Windows.

## <a name="code-analysis"></a>Analýza kódu

- Analýza kódu se teď spouští automaticky na pozadí. Upozornění se v editoru během psaní podtrhávají zelenou vlnovkou. Další informace naleznete v tématu [Analýza kódu v editoru v aplikaci Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/in-editor-code-analysis-in-visual-studio-2019-preview-2/).

- Nová experimentální pravidla ConcurrencyCheck pro dobře známé standardní typy knihoven z hlavičky > mutex \<. Další informace naleznete v tématu [Analýza kódu souběžnosti v aplikaci Visual Studio 2019](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/).

- Aktualizovaná Částečná implementace [kontroly profilu životnosti](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/), která detekuje ukazatele dangling a odkazy. Další informace najdete v tématu [aktualizace profilu životnosti v aplikaci Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/).

- Další kontroly související s korutinou, včetně C26138, C26810, C26811 a experimentálního pravidla C26800. Další informace naleznete v tématu [nové kontroly analýzy kódu v aplikaci Visual Studio 2019: použití za přesunutí a korutina](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/).

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 verze 16,1

- Nové rychlé opravy pro neinicializované kontroly proměnných. Další informace najdete v tématu [nové opravy pro analýzu kódu pro neinicializovaná paměť (C6001) a použití před upozorněními init (C26494)](https://devblogs.microsoft.com/cppblog/new-code-analysis-quick-fixes-for-uninitialized-memory-c6001-and-use-before-init-c26494-warnings/).

## <a name="unit-testing"></a>Testování jednotek

Šablona spravovaného testovacího projektu C++ už není dostupná. Můžete pokračovat v používání spravovaného C++ testovacího rozhraní ve stávajících projektech. Pro nové testy jednotek zvažte použití jednoho z nativních testovacích rozhraní, pro které aplikace Visual Studio poskytuje šablony (MSTest, Google Test) nebo šablonu spravovaného C# testovacího projektu.

::: moniker-end

::: moniker range="=vs-2017"

Visual Studio 2017 přináší mnoho aktualizací a oprav do C++ prostředí. Opravili jsme víc než 250 chyb a nahlásili problémy v kompilátorech a nástrojích, mnoho odeslaných zákazníky prostřednictvím [nahlášení problému a nabízí návrhy](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2017) v části **odeslání zpětné vazby**. Děkujeme vám, že hlásíte chyby! Další informace o tom, co je nového ve všech verzích sady Visual Studio, naleznete v tématu [co je nového v aplikaci Visual studio 2017](/visualstudio/ide/whats-new-visual-studio-2017?view=vs-2017). Informace o tom, co je nového C++ v aplikaci visual Studio 2019, najdete v tématu [co C++ je nového v aplikaci Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019). Informace o tom, co je nového C++ v aplikaci Visual Studio 2015 a dřívějších verzích, najdete v článku [ C++ co je nového 2003 až 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="c-compiler"></a>kompilátor C++

### <a name="c-conformance-improvements"></a>C++vylepšení shody

V této verzi jsme kompilátor jazyka C++ a standardní knihovny doplnili rozšířenou podporou pro funkce C++11 a C++14, a také předběžnou podporou pro některé funkce očekávané ve standardu C++17. Podrobné informace naleznete v tématu [ C++ vylepšení shody v aplikaci Visual Studio 2017](cpp-conformance-improvements.md).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15,5

Kompilátor podporuje přibližně 75% funkcí, které jsou v C++ 17 novinkou, včetně strukturovaných vazeb, `constexpr` výrazů lambda, `if constexpr`, vložených proměnných, výrazů skládání a přidání `noexcept` do systému typů. Tyto funkce jsou k dispozici v rámci možnosti **/std: c++ 17** . Další informace najdete v tématu [ C++ vylepšení shody v aplikaci Visual Studio 2017.](cpp-conformance-improvements.md)

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15,7

Sada nástrojů kompilátoru MSVC v sadě Visual Studio verze 15,7 teď vyhovuje C++ standardu. Další informace najdete v tématu [oznamujeme: MSVC odpovídá C++ standardu](https://devblogs.microsoft.com/cppblog/announcing-msvc-conforms-to-the-c-standard/) a [jazyku jazyka Microsoft C++ ](../visual-cpp-language-conformance.md).

##### <a name="visual-studio-2017-version-158"></a>Visual Studio 2017 verze 15,8

Přepínač kompilátoru [/Experimental: preprocesor](../build/reference/experimental-preprocessor.md) umožňuje nové experimentální MSVC preprocesoru, který bude nakonec odpovídat všem použitelným normám jazyka C a C++ . Další informace najdete v tématu [MSVC experimentální preprocesor – přehled](../preprocessor/preprocessor-experimental-overview.md).

### <a name="new-compiler-options"></a>Nové možnosti kompilátoru

- [/Permissive-](../build/reference/permissive-standards-conformance.md): povolení všech striktních standardních možností kompilátoru a zakázání většiny rozšíření kompilátoru specifických pro společnost Microsoft (ale ne `__declspec(dllimport)`, například). Tato možnost je ve výchozím nastavení zapnuta v aplikaci Visual Studio 2017 verze 15,5.  Režim **/Permissive-** odpovídá podpoře vyhledávání názvů ve dvou fázích. Další informace najdete v tématu [ C++ vylepšení shody v aplikaci Visual Studio](cpp-conformance-improvements.md).

- [/Diagnostics](../build/reference/diagnostics-compiler-diagnostic-options.md): umožňuje zobrazit číslo řádku, číslo řádku a sloupec nebo číslo řádku a sloupec a blikající kurzor pod řádkem kódu, kde se našla diagnostická chyba nebo upozornění.

- [/debug: FastLink](../build/reference/debug-generate-debug-info.md): povolí až 30% rychlejších přírůstkových propojení (vs. Visual Studio 2015) tím, že se nekopírují všechny ladicí informace do souboru PDB. Soubor PDB místo toho odkazuje na ladicí informace pro objekty a soubory knihovny použité k vytvoření spustitelného souboru. Podívejte se na [rychlejší C++ cyklus sestavení v vs "15" s/Debug: FastLink](https://devblogs.microsoft.com/cppblog/faster-c-build-cycle-in-vs-15-with-debugfastlink/) a [doporučeními pro zrychlení C++ sestavení v sadě Visual Studio](https://devblogs.microsoft.com/cppblog/recommendations-to-speed-c-builds-in-visual-studio/).

- Visual Studio 2017 umožňuje použití [/SDL](../build/reference/sdl-enable-additional-security-checks.md) s [/await](../build/reference/await-enable-coroutine-support.md). Odebrali jsme omezení [/RTC](../build/reference/rtc-run-time-error-checks.md) s korutinami.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15,3

- [/std: c++ 14 a/std: c + + nejnovější](../build/reference/std-specify-language-standard-version.md): tyto možnosti kompilátoru vám umožňují odhlásit se ke konkrétním verzím programovacího C++ jazyka ISO v projektu. Většina nových konceptů nových funkcí je chráněná možností **/std: c + + nejnovější** .

- [/std: c++ 17](../build/reference/std-specify-language-standard-version.md) umožňuje sadu funkcí c++ 17 implementovaných kompilátorem. Tato možnost zakáže podporu kompilátoru a standardní knihovny pro funkce, které jsou změněny nebo novinkou ve verzích pracovního konceptu a aktualizacích chyb C++ Standard po c++ 17. Pokud chcete tyto funkce povolit, použijte **/std: c + + nejnovější**.

### <a name="codegen-security-diagnostics-and-versioning"></a>CodeGen, zabezpečení, diagnostika a správa verzí

Tato vydaná verze přináší několik vylepšení optimalizace, generování kódu, správu verzí sady nástrojů a diagnostiku. Mezi důležitá vylepšení patří:

- Vylepšené generování kódu smyček: Podpora automatické vektorizace dělení konstantních celých čísel, lepší identifikace vzorů memset
- Vylepšené zabezpečení kódu: Vylepšená emise diagnostiky kompilátoru přetečení vyrovnávací paměti a [/Guard: CF](../build/reference/guard-enable-control-flow-guard.md) teď chrání příkazy Switch, které generují tabulky skoků.
- Správa verzí: hodnota předdefinovaného makra preprocesoru **\_MSC\_ver** se teď rovnoměrně zvětšující aktualizuje při každé aktualizaci sady nástrojů Visual C++ . Další informace naleznete v tématu [Visual C++ Compiler Version](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/).
- Nové rozložení sady nástrojů: kompilátor a související nástroje sestavení mají na svém vývojovém počítači nové umístění a strukturu adresářů. Nové rozložení umožňuje souběžnou instalaci více verzí kompilátoru. Další informace naleznete v tématu [rozložení nástrojů kompilátoru v aplikaci Visual Studio 2017](https://devblogs.microsoft.com/cppblog/compiler-tools-layout-in-visual-studio-15/).
- Vylepšená diagnostika: okno výstup nyní zobrazuje sloupec, ve kterém došlo k chybě. Další informace najdete v tématu [ C++ vylepšení diagnostiky kompilátoru v sadě vs "15" Preview 5](https://devblogs.microsoft.com/cppblog/c-compiler-diagnostics-improvements-in-vs-15-rc/).
- Při použití korutiny se odebraly **klíčové slovo** experimentální (k dispozici v rámci možnosti **/await** ). Váš kód by měl být aktualizován, aby místo toho používal `co_yield`. Další informace najdete v tématu [`yield` klíčového slova, které se má `co_yield` v sadě VS 2017](https://devblogs.microsoft.com/cppblog/yield-keyword-to-become-co_yield-in-vs-2017/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15,3

Další vylepšení diagnostiky v kompilátoru. Další informace najdete v tématu [vylepšení diagnostiky v aplikaci Visual Studio 2017 15.3.0](https://devblogs.microsoft.com/cppblog/diagnostic-improvements-in-vs2017-15-3-0/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15,5

Výkon C++ vizuálního modulu runtime je nadále vylepší kvůli lepšímu vygenerování kvality kódu. Nyní můžete znovu kompilovat kód a aplikace je spouštěna rychleji. Některé optimalizace kompilátoru jsou zcela nové, například vektory podmíněných skalárních úložišť, kombinování volání `sin(x)` a `cos(x)` do nového `sincos(x)`a eliminace nadbytečných instrukcí z Optimalizátoru SSA. Další optimalizace kompilátoru jsou vylepšení stávajících funkcí, jako jsou vektorizace heuristiky pro podmíněné výrazy, lepší optimalizace smyček a minimální počet codegenů typu float. Linker má nové a rychlejší **/OPT: implementace brány firewall** , což může způsobit až 9% urychleníí v době propojení a další opravy výkonu v přírůstkovém propojování. Další informace najdete v tématu [/opt (optimalizace)](../build/reference/opt-optimizations.md) a [/incremental (propojování přírůstkově)](../build/reference/incremental-link-incrementally.md).

Kompilátor společnosti C++ Microsoft podporuje procesory Intel AVX-512, včetně instrukcí pro délku vektoru, které přinášejí nové funkce v AVX-512 na 128-bitové 256 a 16bitové Registry v rámci.

Parametr [/Zc: noexceptTypes-](../build/reference/zc-noexcepttypes.md) lze použít pro návrat k verzi c++ 14 `noexcept` Při obecném použití režimu c++ 17. Tato možnost umožňuje aktualizovat zdrojový kód tak, aby odpovídal C++ 17 bez nutnosti přepisování kódu `throw()` ve stejnou dobu. Další informace naleznete v tématu [odstranění specifikace dynamické výjimky a s výjimkou](cpp-conformance-improvements.md#noexcept_removal).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15,7

- Nový přepínač kompilátoru [/Qspectre](../build/reference/qspectre.md) , který se může zmírnit proti spekulativním útokům na straně vykonání kanálu. Další informace najdete v tématu [zmírnění hrozeb Spectre v MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).
- Nové diagnostické upozornění pro zmírnění rizik Spectre Další informace najdete v tématu [Diagnostika Spectre ve Visual studiu 2017 verze 15,7 Preview 4](https://devblogs.microsoft.com/cppblog/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/).
- Nová hodnota parametru/Zc, **/Zc: __cplusplus**umožňuje správné vytváření sestav C++ standardní podpory. Například když je přepínač nastaven a kompilátor je v/std: režim c++ 17, hodnota se rozšíří na **201703L**. Další informace najdete v článku [MSVC nyní správně hlásí __cplusplus](https://devblogs.microsoft.com/cppblog/msvc-now-correctly-reports-__cplusplus/).

## <a name="c-standard-library"></a>C++Standardní knihovna

### <a name="correctness-improvements"></a>Vylepšení správnosti

##### <a name="visual-studio-2017-rtm-version-150"></a>Visual Studio 2017 RTM (verze 15,0)

- Menší `basic_string` vylepšení `_ITERATOR_DEBUG_LEVEL != 0` diagnostiky. Přeskočení kontroly IDL v sadě řetězců teď oznámí konkrétní chování, které toto přeskočení způsobilo. Například místo zprávy oznamující, že iterátor řetězce nejde přesměrovat, se teď zobrazí zpráva s oznámením, že iterátor řetězce nejde přesměrovat, protože je mimo rozsah (např. je to koncový iterátor).
- Opravili jsme operátor přiřazení `std::promise` přesunutí, který dřív mohl způsobit, že se kód trvale zablokuje.
- Opravily se chyby kompilátoru s `atomic<T*>` implicitním převodem na `T*`.
- `pointer_traits<Ptr>` nyní správně detekuje `Ptr::rebind<U>`.
- V operátoru odčítání `move_iterator` byl opraven chybějící kvalifikátor `const`.
- Opravili jsme tiché chybné CodeGen pro stavová uživatelsky definovaná přidělování, která žádají `propagate_on_container_copy_assignment` a `propagate_on_container_move_assignment`.
- `atomic<T>` nyní tolerována přetížená `operator&()`.
- Mírně Vylepšená Diagnostika kompilátoru pro nesprávná `bind()` volání.

Úplný seznam standardních vylepšení knihovny v sadě Visual Studio 2017 RTM najdete v tématu věnovaném C++ [opravám Standard knihovny na blogu týmu v sadě vs 2017 RTM](https://devblogs.microsoft.com/cppblog/stl-fixes-in-vs-2017-rtm/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15,3

- Knihovny standardních knihoven teď do `numeric_limits<difference_type>::max()` místo `max()` `size_type`přitlačí jejich `max_size()`. Tato změna zajistí, že výsledek `distance()` na iterátorech z tohoto kontejneru je reprezentovatelné v návratovém typu `distance()`.
- Opravila se chybějící `auto_ptr<void>`specializace.
- Rozhraní `for_each_n()`, `generate_n()`a `search_n()` se dřív nepodařilo zkompilovat, pokud argument Length není integrálního typu; Nyní se pokusí převést neintegrální délky na `difference_type`iterátory.
- `normal_distribution<float>` už negeneruje upozornění v rámci standardní knihovny o zúžení z Double na float.
- Opravili jsme některé `basic_string` operace, které se při kontrole maximální velikosti přetečení používají `npos` místo `max_size()`.
- `condition_variable::wait_for(lock, relative_time, predicate)` by čekala na celý relativní čas v případě spurious Wake. Nyní bude čekat pouze na jeden interval relativního času.
- `future::get()` nyní neověřuje `future`, jak vyžaduje standard.
- `iterator_traits<void *>` použito k tomu, že došlo k závažné chybě, protože se pokusila vytvořit `void&`; Nyní se vyčistit jako prázdná struktura, aby bylo možné použít `iterator_traits` v podmínkách "je iterátor" SFINAE podmínky.
- Některá upozornění oznámená Clang **-Wsystem-Headers** byla opravena.
- Také opravená "specifikace výjimky v deklaraci neodpovídá předchozí deklaraci" hlášené pomocí Clang **-Wmicrosoft-Exception-spec**.
- Také opravená upozornění na řazení mem-inicializátor-list hlášená Clang a C1XX.
- Neuspořádané kontejnery neměnily své funkce hash nebo predikáty, pokud byly samotné kontejnery prohozeny. Teď to dělají.
- Mnoho operací prohození kontejnerů je nyní označeno jako `noexcept` (protože naše standardní knihovna nikdy nechce vyvolat výjimku při zjišťování nedefinovaného stavu nedefinovaného ne`propagate_on_container_swap`ho přidělujícího modulu přidělování, který nerovná se).
- Mnoho `vector<bool>` operací se teď označilo jako `noexcept`.
- Standardní knihovna nyní vynutilí odpovídajícího `value_type` přidělování (v režimu C++ 17) s řídicím šrafováním pro výslovný souhlas.
- Opravili jsme některé podmínky, kdy by `basic_string` v rámci rozsahu vložení do zakódovat obsah řetězců. (Poznámka: pole pro vložení do rozsahu je stále zakázáno standardem.)
- `basic_string::shrink_to_fit()` už neovlivňuje `propagate_on_container_swap`přidělování.
- `std::decay` nyní zpracovává typy funkcí Abominable, to znamená typy funkcí, které jsou kvalifikovány a/nebo určené k odkazu.
- Změněné direktivy include pro použití správných citlivostí velkých a malých písmen a lomítka, zlepšení přenositelnosti.
- Pevné upozornění C4061 "enumerátor '*enumerátor*' v přepínači*výčtu ' enum ' není*explicitně zpracováno jmenovkou Case". Toto upozornění je vypnuto – ve výchozím nastavení a bylo opraveno jako výjimka pro obecné zásady standardní knihovny pro upozornění. (Standardní knihovna je **/W4** vyčistit, ale nepokusí se **/Wall** vyčistit. Mnoho dalších výchozích varování je mimořádně vysoce velké a není určené k pravidelnému používání.)
- Vylepšené kontroly ladění `std::list`. Seznam iterátorů nyní kontroluje `operator->()`a `list::unique()` nyní označuje iterátory jako neověřené.
- Pevná použití metaprogramování šablonou pro přidělování v `tuple`.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15,5

- `std::partition` nyní volá predikát N namísto N + 1 krát, jak vyžaduje standard.
- Pokusy o zamezení Magic static ve verzi 15,3 byly opraveny ve verzi 15,5.
- `std::atomic<T>` už nevyžadují, aby `T` výchozí constructible.
- Algoritmy haldy, které přijímají logaritmický čas, již nedělají lineární časový kontrolní výraz, který je ve skutečnosti haldou, když je povoleno ladění iterátoru.
- `__declspec(allocator)` je teď chráněná jenom pro C1XX, aby se zabránilo varováním z Clang, které nerozumí tomuto declspec.
- `basic_string::npos` je nyní k dispozici jako časová konstanta kompilace.
- `std::allocator` v režimu C++ 17 nyní správně zpracovává přidělení nadrovnaných typů, to znamená typy, jejichž zarovnání je větší než `max_align_t`, pokud není zakázáno parametrem **/Zc: alignedNew-** .  Například vektory objektů se zarovnáním na 16 bajtů nebo 32 bajtů jsou nyní správně zarovnány pro instrukce SSE a AVX.

### <a name="conformance-improvements"></a>Vylepšení shody

- Přidali jsme \<\>\<string_view\>, `apply()``make_from_tuple()`.
- Přidání \<volitelné\>, \<variant\>, `shared_ptr::weak_type`a \<cstdalign\>.
- Povolena `constexpr` C++ 14 v `min(initializer_list)`, `max(initializer_list)`a `minmax(initializer_list)`a `min_element()`, `max_element()`a `minmax_element()`.

Další informace najdete v tématu [tabulka C++ pro shodu jazyka Microsoft](../visual-cpp-language-conformance.md).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15,3

- Bylo implementováno několik dalších funkcí C++ 17. Další informace najdete v tématu [tabulka C++ pro shodu jazyka Microsoft](cpp-conformance-improvements.md#improvements_153).
- Implementovaná P0602R0a "variant a Optional by měla rozšířit triviální možnost kopírování/přesunutí".
- Standardní knihovna nyní umožňuje úředně tolerovat dynamickou RTTI zakázanou prostřednictvím možnosti [/gr-](../build/reference/gr-enable-run-time-type-information.md) . `dynamic_pointer_cast()` i `rethrow_if_nested()` v podstatě vyžadují `dynamic_cast`, takže ji standardní knihovna nyní označí jako `=delete` v rámci **/gr-** .
- I v případě, že byl dynamický RTTI zakázán prostřednictvím **/gr-** , "static RTTI" ve formě `typeid(SomeType)` je stále k dispozici a má několik standardních komponent knihovny. Standardní knihovna teď podporuje vypnutí této funkce, a to prostřednictvím **/d\_má\_statické\_RTTI = 0**. Tento příznak také zakáže `std::any`, `target()` a `target_type()` členských funkcí `std::function`a `get_deleter()` členské funkce Friend `std::shared_ptr` a `std::weak_ptr`.
- Standardní knihovna nyní používá C++ 14 `constexpr` bezpodmínečně namísto podmíněně definovaných maker.
- Standardní knihovna nyní používá šablony aliasu interně.
- Standardní knihovna nyní používá `nullptr` interně místo `nullptr_t{}`. (Bylo vyhubeno vnitřní použití hodnoty NULL. Vnitřní použití 0-as-null se vyčistí postupně.)
- Standardní knihovna nyní používá `std::move()` interně místo stylistické použití `std::forward()`.
- Změna `static_assert(false, "message")` na `#error message`. Tato změna vylepšuje diagnostiku kompilátoru, protože `#error` okamžitě zastaví kompilaci.
- Standardní knihovna již neoznačuje funkce jako `__declspec(dllimport)`. Technologie moderního linkeru už to nevyžaduje.
- Extrahována SFINAE k výchozím argumentům šablony, což snižuje množství zbytečných hodnot v porovnání s návratovými typy a typy argumentů funkce.
- Kontrola ladění v \<náhodným\> teď místo interní `_Rng_abort()` funkce, která se nazývá `fputs()` až **stderr**, použít běžné strojní zařízení standardní knihovny. Implementace této funkce je uchována v případě binární kompatibility, ale byla odebrána v další binární nekompatibilní verzi standardní knihovny.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15,5

- V souladu s normou C++ 17 se přidaly, zastaraly nebo odebraly některé standardní funkce knihovny. Další informace najdete v tématu [ C++ vylepšení shody v aplikaci Visual Studio](cpp-conformance-improvements.md#improvements_155).
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
- Signatury pro následující paralelní algoritmy jsou přidány, ale nejsou v tuto chvíli paralelní. profilace ukázala, že v algoritmech virtuálního nejsou žádné výhody, které přesouvají nebo permute – prvky:
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

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 verze 15,6

- \<memory_resource >
- Základy knihovny v1
- Odstraňuje se přiřazení `polymorphic_allocator`.
- Vylepšení srážek argumentu šablony třídy

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15,7

- Podpora paralelních algoritmů už není experimentální.
- Nová implementace \<systému souborů >
- Základní převody řetězců (částečné)
- `std::launder()`
- `std::byte`
- `hypot(x,y,z)`
- Předcházení zbytečným Decay
- Matematické speciální funkce
- `constexpr char_traits`
- Průvodci odpočty pro standardní knihovnu

Další informace najdete v tématu [tabulka C++ pro shodu jazyka Microsoft](../visual-cpp-language-conformance.md).

### <a name="performance-and-throughput-fixes"></a>Opravy výkonu a propustnosti

- Provedeno `basic_string::find(char)` přetížení volá `traits::find` pouze jednou. Dříve byla implementována jako obecná řetězcová hledání pro řetězec o délce 1.
- `basic_string::operator==` nyní před porovnáním obsahu řetězců kontroluje velikost řetězce.
- Bylo odebráno propojení ovládacího prvku v `basic_string`, což bylo pro Optimalizátor kompilátoru obtížné analyzovat. U všech krátkých řetězců volání `reserve` stále nemá žádné nenulové náklady, aby nedošlo k žádnému provedení.
- `std::vector` se převedlo na správnost a výkon: vytváření aliasů během operací vložení a emplace je teď správně zpracované podle požadavků standardu. Záruka silné výjimky se teď poskytuje, pokud to vyžaduje standard přes `move_if_noexcept()` a jiné. Logic a INSERT a emplace provádějí méně operací elementu.
- C++ Standardní knihovna teď nevylučuje přesměrování na ozdobné ukazatele s hodnotou null.
- Vylepšený výkon `weak_ptr::lock()`.
- Aby se zvýšila propustnost C++ kompilátoru, standardní hlavičky knihovny teď zabraňují deklaracím, aby nedocházelo k nepotřebným vnitřním překladačům.
- Vylepšili jsme výkon `std::string` a `std::wstring` přesunout konstruktory o více než třikrát.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15,3

- Pracovaly kolem interakcí s `noexcept`, které znemožňují vkládání `std::atomic` implementace do funkcí, které používají strukturované zpracování výjimek (SEH).
- Byla změněna interní funkce `_Deallocate()` standardní knihovny pro optimalizaci do menšího kódu, což umožňuje jejich inlineování na více místech.
- Místo rekurze došlo ke změně `std::try_lock()` k použití rozšíření balíčku.
- Vylepšili `std::lock()` algoritmus zamezení zablokování pro použití `lock()`ch operací místo toho, aby se na všech zámkech neotáčí `try_lock()`.
- Byla povolena optimalizace pojmenované návratové hodnoty v `system_category::message()`.
- `conjunction` a `disjunction` nyní vytváří instance N + 1 typů, nikoli 2N + 2 typy.
- `std::function` už nevytváří instanci mechanismů podpory přidělování pro každý vyměnitelný typ, zlepšuje propustnost a zmenšuje velikost. obj v programech, které do `std::function`předají mnoho různých výrazů lambda.
- `allocator_traits<std::allocator>` obsahuje ručně vložené `std::allocator` operace, čímž se zmenší velikost kódu v kódu, který komunikuje s `std::allocator` pouze prostřednictvím `allocator_traits` (tj. ve většině kódu).
- Rozhraní s minimálním přidělováním C++ 11 je teď zpracováváno standardní knihovnou volání `allocator_traits` přímo místo zabalení přidělování do interní `_Wrap_alloc`třídy. Tato změna snižuje velikost kódu vygenerovaného pro podporu přidělování, zlepšuje v některých případech možnost Optimalizátoru v případě knihoven standardních knihoven a nabízí lepší možnosti ladění (teď, když vidíte typ přidělování místo `_Wrap_alloc<your_allocator_type>` v ladicí program).
- Odebrali jsme metaprogramování šablonou pro přizpůsobená `allocator::reference`, která přidělování ve skutečnosti neumožňují přizpůsobení. (Alokátory můžou kontejnery používat ozdobné ukazatele, ale ne ozdobné odkazy.)
- Front-end kompilátor byl výukou pro rozbalení iterátorů ladění v rámci smyček na základě rozsahu, což vylepšuje výkon sestavení ladění.
- `basic_string` interní cesta zmenšení pro `shrink_to_fit()` a `reserve()` již není v cestě k přerozdělení operací, čímž se zmenší velikost kódu pro všechny ostatní členy.
- Cesta k internímu zvětšení `basic_string` již není v cestě k `shrink_to_fit()`.
- `basic_string`é operace jsou nyní přizpůsobené nepřidělením rychlé cesty a přidělení pomalých funkcí cest. díky tomu je pravděpodobnější, že běžný případ bez opětovného přidělení nebudete muset být vložen do volajících.
- `basic_string`ící operace nyní vytvoří znovu přidělené vyrovnávací paměti v požadovaném stavu, nikoli Změna velikosti. Například vložení na začátek řetězce nyní přesune obsah po vložení přesně jednou (buď dolů nebo do nově přidělené vyrovnávací paměti), nikoli dvakrát v opačném případě v případě přerozdělení (do nově přidělené vyrovnávací paměti a pak dolů).
- Operace, které volají standardní knihovnu jazyka C v \<řetězec\> nyní mají v mezipaměti `errno`ou adresu pro odebrání opakované interakce s protokolem TLS.
- Zjednodušená implementace `is_pointer`.
- Změna výrazu založeného na funkci SFINAE na `struct` a na základě `void_t`.
- Standardní algoritmy knihovny nyní zabraňují iterátorům postincrementing.
- Pevná upozornění zkrácení při použití 32ho přidělování bitů na 64 systémech.
- přiřazení `std::vector` přesunu je teď efektivnější v případě nerovnosti v případě, kdy je to možné, pomocí vyrovnávací paměti, která je POCMA.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15,5

- `basic_string<char16_t>` nyní zahájí stejné `memcmp`, `memcpy`a podobné optimalizace, které `basic_string<wchar_t>` zapojení.
- Omezení Optimalizátoru, které zabránilo vloženému ukazatelům na funkce v systému Visual Studio 2015 Update 3, bylo využíváno v době, kdy byl obnoven výkon `lower_bound(iter, iter, function pointer)`.
- Režie pro ověření vstupu `includes`, `set_difference`, `set_symmetric_difference`a `set_union` byla snížena o režii při vyřazení iterátorů před zaškrtnutím pořadí.
- `std::inplace_merge` nyní přeskočí prvky, které již jsou na pozici.
- Sestavování `std::random_device` už nevytváří konstrukce a pak zničí `std::string`.
- `std::equal` a `std::partition` měly průchod s optimalizací pro dělení na vlákna, který ukládá porovnání iterátoru.
- Pokud je `std::reverse` předána ukazatelům na triviální kopii `T`, bude nyní zaslána do ručně určené vektorové implementace.
- `std::fill`, `std::equal`a `std::lexicographical_compare` byly výukové postupy odeslání na `memset` a `memcmp` pro `std::byte` a `gsl::byte` (a další výčty podobné typu char a třídy výčtu). Vzhledem k tomu, že `std::copy` odesílá pomocí `is_trivially_copyable`, nepotřebujete žádné změny.
- Standardní knihovna už neobsahuje destruktory prázdných závorek, jejichž typy by měly být jenom triviální – zničitelné.

## <a name="other-libraries"></a>Jiné knihovny

### <a name="open-source-library-support"></a>Podpora open source knihovny

**Vcpkg** je open source nástroj pro příkazový řádek, který výrazně zjednodušuje proces získání a vytváření open source C++ statických knihovny a knihoven DLL v aplikaci Visual Studio. Další informace najdete v tématu [vcpkg: Správce balíčků pro C++ ](../build/vcpkg.md).

### <a name="cpprest-sdk-290"></a>CPPRest SDK 2.9.0

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15,5

Rozhraní Web API pro různé platformy pro C++CPPRestSDK bylo aktualizováno na verzi 2.9.0. Další informace najdete v tématu [CppRestSDK 2.9.0 je k dispozici na GitHubu](https://devblogs.microsoft.com/cppblog/cpprestsdk-2-9-0-is-available-on-github/).

### <a name="atl"></a>ATL

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15,5

- Ještě další sada oprav shody názvů – vyhledávání
- Existující konstruktory přesunutí a operátory přiřazení přesunu jsou teď správně označené jako nevyvolání.
- Zrušení potlačení platných upozornění C4640 týkajícího o bezpečné inicializaci vlákna místních statických hodnot v atlstr. h
- Inicializace místních statických proměnných v rámci vlákna byla v sadě nástrojů XP automaticky vypnuta při použití ATL k sestavení knihovny DLL, ale nyní není. Můžete přidat parametr **/Zc: threadSafeInit-** v nastavení projektu, pokud je požadováno inicializaci bezpečné pro přístup z více vláken.

### <a name="visual-c-runtime"></a>Visual C++ runtime

- New header "cfguard. h" pro symboly ochrany toku řízení.

## <a name="c-ide"></a>C++ IDE

- Výkon při změně konfigurace je teď vyšší u nativních projektů C++ a mnohem vyšší u projektů C++/CLI. Když se konfigurace řešení aktivuje poprvé, bude se teď zrychlit a všechny pozdější Aktivace této konfigurace řešení budou skoro okamžité.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15,3

- Několik průvodců projektu a kódu je přepsaných ve stylu dialogu podpisu.
- **Přidat třídu** nyní spustí Průvodce přidáním třídy přímo. Všechny ostatní položky, které byly dříve tady, jsou teď dostupné v části **přidat > novou položku**.
- Projekty Win32 jsou nyní pod kategorií **Desktop systému Windows** v dialogovém okně **Nový projekt** .
- Šablony **konzolové** aplikace pro Windows a **aplikace klasické pracovní plochy** nyní vytvářejí projekty bez zobrazení průvodce. V rámci stejné kategorie je k dispozici nový **Průvodce pracovní plocha systému Windows** , ve kterém se zobrazují stejné možnosti jako původní průvodce **konzolové aplikace Win32** .

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15,5

Několik C++ operací, které používají modul IntelliSense pro refaktoring a navigaci v kódu, se spouští mnohem rychleji. Následující čísla jsou založena na řešení Visual Studio chrom s 3500 projekty:

|||
|-|-|
|Funkce|Zlepšení výkonu|
|přejmenování|5.3 x|
|Změnit signaturu |4.5 x|
|Najít všechny odkazy|4.7 x|

C++nyní podporuje kombinaci kláves Ctrl + kliknutí **Přejít k definici**, která usnadňuje navigaci myši na definice. Ve výchozím nastavení je teď součástí produktu i Vizualizér struktury ze sady Power nástrojů pro produktivitu.

## <a name="intellisense"></a>IntelliSense

- Ve výchozím nastavení je nyní používán nový databázový stroj využívající SQLite. Tím se urychlí databázové operace jako **Přejít k definici** a **hledání všech odkazů**a výrazně se tím zkrátí doba analýzy počátečního řešení. Toto nastavení se přesunulo do **nástrojů > možnosti > textový Editor > C/C++ > Advanced** (dříve se jednalo o... C/C++ | Experimentální).

- Vylepšili jsme výkon technologie IntelliSense v projektech a souborech, které nepoužívají předkompilované hlavičky – pro hlavičky aktuálního souboru se vytvoří Automatická Předkompilovaná hlavička.

- Přidali jsme do seznamu chyb filtrování a nápovědu k chybám technologie IntelliSense. Kliknutí na sloupec s chybami teď umožní je filtrovat. Kromě toho kliknutím na konkrétní chyby nebo stisknutím klávesy F1 spustíte online vyhledávání chybové zprávy.

  ![Seznam chyb](media/ErrorList1.png "Seznam chyb")

  ![Filtrované Seznam chyb](media/ErrorList2.png "Filtrovaný seznam chyb")

- Přidali jsme možnost filtrovat položky seznamu členů podle typu.

  ![Filtrování seznamu členů](media/mlfiltering.png "Filtrování seznamu členů")

- Přidali jsme novou experimentální funkci prediktivní technologie IntelliSense, která poskytuje kontextově závislé filtrování toho, co se zobrazuje v seznamu členů. Další informace najdete v tématu [ C++ vylepšení technologie IntelliSense – prediktivní IntelliSense & filtrování](https://devblogs.microsoft.com/cppblog/c-intellisense-improvements-predictive-intellisense-filtering/).
- **Najít všechny odkazy** (SHIFT + F12) nyní usnadňuje snadnou navigaci, a to i v komplexních základech kódu. Poskytuje pokročilé seskupení, filtrování, řazení, hledání v rámci výsledků a (u některých jazyků), takže můžete získat jasné informace o svých odkazech. C++V případě nástroje obsahuje nové uživatelské rozhraní informace o tom, zda čteme nebo zapisujeme do proměnné.
- Funkce změny tečky na šipku technologie IntelliSense se změnila z experimentální na pokročilou a teď je ve výchozím nastavení povolená. Funkce editoru **rozšiřují obory** a zároveň se přesunula **Priorita** z experimentální na pokročilou.
- Funkce experimentálního refaktoringu **změnit signaturu** a **extrahovat funkci** jsou teď ve výchozím nastavení dostupné.
- Bylo přidáno experimentální funkce rychlejšího načítání projektů pro C++ projekty. Při příštím otevření C++ projektu se načtou rychleji a čas po jeho načtení bude *mnohem* rychlejší.
- Některé z těchto funkcí jsou společné pro jiné jazyky a některé jsou specifické pro C++. Další informace o těchto nových funkcích naleznete v tématu [oznamujeme vydání sady Visual Studio "15" Preview 5](https://devblogs.microsoft.com/visualstudio/announcing-visual-studio-15-preview-5/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15,7

- Byla přidána podpora pro ClangFormat. Další informace najdete v tématu [Podpora ClangFormat v aplikaci Visual Studio 2017](https://devblogs.microsoft.com/cppblog/clangformat-support-in-visual-studio-2017-15-7-preview-1/).

## <a name="non-msbuild-projects-with-open-folder"></a>Projekty jiného typu než MSBuild s otevřenou složkou

Visual Studio 2017 zavádí funkci **otevřené složky** , která umožňuje kódování, sestavení a ladění ve složce obsahující zdrojový kód bez nutnosti vytvářet žádná řešení nebo projekty. Nyní je mnohem jednodušší začít se sadou Visual Studio, a to i v případě, že projekt není projekt založený na MSBuildu. Díky **otevřené složce**získáte přístup k výkonným funkcím pro porozumění, úpravám, sestavování a ladění kódu, které už Visual Studio poskytuje pro projekty MSBuild. Další informace naleznete v tématu [Otevřít složku projekty pro C++ ](../build/open-folder-projects-cpp.md).

- Vylepšení prostředí Otevřít složku Můžete přizpůsobit prostředí pomocí těchto souborů. JSON:
  - CppProperties.json použijte k přizpůsobení technologie IntelliSense a prostředí procházení.
  - Tasks.json použijte k přizpůsobení kroků sestavení.
  - Launch.json použijte k přizpůsobení prostředí ladění.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15,3

- Vylepšená podpora alternativních kompilátorů a prostředí pro sestavování, jako jsou MinGW a Cygwin. Další informace najdete v tématu [použití MinGW a Cygwin s vizuální C++ a otevřenou složkou](https://devblogs.microsoft.com/cppblog/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/).
- Přidání podpory pro definování globálních a specifických proměnných prostředí specifických pro konfiguraci v CppProperties. JSON a CMakeSettings. JSON. Tyto proměnné prostředí lze spotřebovat pomocí konfigurací ladění definovaných v příkazu Launch. vs. JSON a úkoly v Tasks. vs. JSON. Další informace najdete v tématu [přizpůsobení prostředí pomocí vizuální C++ a otevřené složky](https://devblogs.microsoft.com/cppblog/customizing-your-environment-with-visual-c-and-open-folder/).
- Vylepšená podpora generátoru expertem CMake, včetně možnosti snadno cílit na 64 bitů na platformě.

## <a name="cmake-support-via-open-folder"></a>Podpora CMake prostřednictvím otevřené složky

Sada Visual Studio 2017 zavádí podporu pro použití projektů CMake bez převodu na soubory projektu MSBuild (. vcxproj). Další informace najdete v tématu [projekty cmake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md). Otevření projektů CMake s **otevřenou složkou** automaticky nakonfiguruje C++ prostředí pro úpravy, sestavování a ladění.

- C++Technologie IntelliSense funguje bez nutnosti vytvořit soubor CppProperties. JSON v kořenové složce. Přidali jsme také nové rozevírací seznam umožňující uživatelům snadno přepínat mezi konfiguracemi poskytovanými soubory CMake a CppProperties. JSON.

- Prostřednictvím souboru CMakeSettings.json, který je umístěný ve stejné složce jako soubor CMakeLists.txt, se podporuje další konfigurace.

  ![Otevřená složka cmake](media/cmake-cpp.png "Otevřená složka CMake")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15,3

- Přidala se podpora pro generátor expertem CMake.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15,5

- Byla přidána podpora pro import existujících mezipamětí CMake.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15,5

- Přidala se podpora pro CMake 3,11, analýza kódu v projektech CMake, zobrazení cílů v Průzkumník řešení, možnosti generování mezipaměti a kompilace jednoho souboru. Další informace najdete v tématu [Podpora cmake v sadě Visual Studio](https://devblogs.microsoft.com/cppblog/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) a [projektech cmake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md).

## <a name="windows-desktop-development-with-c"></a>Vývoj desktopových aplikací pro Windows pomocíC++

Při instalaci původní úlohy pro C++ teď poskytujeme podrobnější prostředí instalace. Přidali jsme volitelné součásti, které vám umožní vybrat a nainstalovat jen ty nástroje, které potřebujete. Uvedené velikosti instalace pro součásti uvedené v uživatelském rozhraní instalačního programu nejsou přesné a podceňují skutečnou celkovou velikost.

Když chcete úspěšně vytvářet projekty Win32 v úloze vývoje desktopových aplikací v C++, musíte nainstalovat sadu nástrojů i sadu Windows SDK. Nainstalujte doporučené (vybrané) komponenty **VC + + 2017 v141 sady nástrojů (x86, x64)** a **Windows 10 SDK (10.0. NNNNN)** , abyste se ujistili, že funguje. Pokud nejsou potřebné nástroje nainstalované, projekty se nevytvoří úspěšně a průvodce se zablokuje.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15,5

Nástroje pro C++ vizuální sestavení (dříve dostupné jako samostatný produkt) jsou teď zahrnuté jako úlohy v instalační program pro Visual Studio. Tato úloha nainstaluje pouze nástroje potřebné pro sestavení C++ projektů bez instalace prostředí IDE sady Visual Studio. Zahrnují se sady nástrojů v140 i v141. Sada nástrojů v141 obsahuje nejnovější vylepšení sady Visual Studio 2017 verze 15,5. Další informace najdete v tématu [Visual Studio Build Tools nyní zahrnují sady nástrojů MSVC a VS2015](https://devblogs.microsoft.com/cppblog/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/).

## <a name="linux-development-with-c"></a>Vývoj pro Linux pomocíC++

Oblíbené rozšíření [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) je teď součástí sady Visual Studio. Tato instalace nabízí všechno, co potřebujete k vývoji a ladění aplikací v jazyce C++, které se spouštějí v prostředí systému Linux.

##### <a name="visual-studio-2017-version-152"></a>Visual Studio 2017 verze 15,2

Vylepšení byla provedená ve sdílení kódu mezi platformami a vizualizací typů. Další informace najdete v tématu [vylepšení C++ Linux pro sdílení kódu pro různé platformy a vizualizaci typů](https://devblogs.microsoft.com/cppblog/linux-cross-platform-and-type-visualization/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15,5

- Úloha Linux přidala podporu pro **rsync** jako alternativu k protokolu **SFTP** pro synchronizaci souborů na vzdálených počítačích se systémem Linux.
- Je přidána podpora pro různé kompilace cílící na mikrokontroléry ARM. Pokud ho chcete v instalaci povolit, zvolte **vývoj pro Linux pomocí C++**  úlohy a vyberte možnost pro **integrovaný vývoj a vývoj IoT**. Tato možnost přidá nástroje pro více kompilačních nástrojů ARM RSZ a provede instalaci. Další informace najdete v tématu o [příčné kompilaci ARM RSZ v sadě Visual Studio](https://devblogs.microsoft.com/cppblog/arm-gcc-cross-compilation-in-visual-studio/).
- Přidala se podpora pro CMake. Teď můžete pracovat na svém stávajícím základu kódu CMake, aniž byste ho museli převádět na projekt sady Visual Studio. Další informace najdete v tématu [konfigurace projektu Linux cmake](../linux/cmake-linux-project.md).
- Byla přidána podpora pro spouštění vzdálených úloh. Tato funkce umožňuje spustit libovolný příkaz ve vzdáleném systému, který je definován ve Správci připojení sady Visual Studio. Vzdálené úlohy také poskytují možnost kopírování souborů do vzdáleného systému.
Další informace najdete v tématu [konfigurace projektu Linux cmake](../linux/cmake-linux-project.md).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15,7

- Různá vylepšení scénářů pro úlohy Linux. Další informace najdete v tématu [vylepšení C++ úloh Linux v systému projektu, okně konzoly pro Linux, rsync a připojení k procesu](https://devblogs.microsoft.com/cppblog/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/).
- Technologie IntelliSense pro záhlaví na vzdálených připojeních systému Linux. Další informace najdete v tématech [technologie IntelliSense pro vzdálené systémy Linux](https://devblogs.microsoft.com/cppblog/intellisense-for-remote-linux-headers/) a [konfigurace projektu pro Linux cmake](../linux/cmake-linux-project.md).

## <a name="game-development-with-c"></a>Vývoj her pomocíC++

Využijte naplno potenciál C++ k vytváření profesionálních her využívajících technologii DirectX nebo Cocos2d.

## <a name="mobile-development-with-c-android-and-ios"></a>Vývoj pro C++ mobilní zařízení (Android a iOS)

Mobilní aplikace teď můžete vytvářet a ladit pomocí sady Visual Studio, která se umí zaměřit i na Android a iOS.

## <a name="universal-windows-apps"></a>Univerzální aplikace pro Windows

C++ je volitelnou součástí úlohy Universal Windows App.  Upgrade projektů C++ se v tuto chvíli musí provést ručně. Pokud otevřete Univerzální platforma Windows projekt cílené na v140 v sadě Visual Studio 2017, je nutné vybrat sadu nástrojů platformy v141 na stránkách vlastností projektu, pokud nemáte nainstalovanou sadu Visual Studio 2015.

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>Nové možnosti pro C++ on Univerzální platforma Windows (UWP)

Nyní máte nové možnosti pro psaní a balení C++ aplikací pro Univerzální platforma Windows a Windows Store: pomocí infrastruktury pro stolní počítače můžete zabalit stávající desktopovou aplikaci nebo objekt com k nasazení prostřednictvím Windows Store nebo přes existující kanály prostřednictvím nasazování po straně. Nové funkce systému Windows 10 umožňují přidat do aplikace klasické pracovní plochy funkce UWP různými způsoby. Další informace najdete v tématu [most pro stolní počítače](/windows/uwp/porting/desktop-to-uwp-root).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15,5

Je přidána šablona projektu pro **balení aplikace systému Windows** , která významně zjednodušuje balení desktopových aplikací s využitím stolního mostu. Je k dispozici v **souboru | Nové | Projekt | Nainstalováno | Vizuál C++ | Univerzální platforma Windows**. Další informace najdete v tématu [sbalení aplikace pomocí sady Visual Studio (most pro stolní počítače)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

Při psaní nového kódu teď můžete použít C++/WinRT, což je standardní C++ jazyková projekce pro prostředí Windows Runtime implementované výhradně v hlavičkových souborech. Umožňuje vytvářet a využívat prostředí Windows Runtime rozhraní API pomocí všech kompilátorů odpovídajících C++ standardům. C++/WinRT je navržený tak C++ , aby poskytoval vývojářům prvotřídní přístup k modernímu rozhraní Windows API. Další informace najdete v tématu [ C++/WinRT: moderní C++ pro prostředí Windows Runtime](https://moderncpp.com/).

Od buildu 17025 Windows SDK Insider Preview je C++/WinRT součástí Windows SDK. Další informace najdete v tématu [ C++/WinRT je teď součástí Windows SDK](https://devblogs.microsoft.com/cppblog/cppwinrt-is-now-included-the-windows-sdk/).

## <a name="clangc2-platform-toolset"></a>Sada nástrojů platformy Clang/C2

Sada nástrojů Clang/C2, která se dodává se sadou Visual Studio 2017, teď podporuje přepínač **/bigobj** , který je rozhodující pro sestavování rozsáhlých projektů. Zahrnuje také několik důležitých oprav chyb, jak ve front-endu, tak v back-endu kompilátoru.

## <a name="c-code-analysis"></a>C++Analýza kódu

Se sadou Visual Studio se nyní distribuují moduly pro kontrolu jádra C++, které vynucují [pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines). Stačí povolit rutiny na stránce **rozšíření pro analýzu kódu** na stránkách vlastností projektu a rozšíření budou zahrnuty při spuštění analýzy kódu. Další informace najdete v tématu [použití C++ hlavních pokynů pro kontrolu](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

![CppCoreCheck](media/CppCoreCheck.png "Stránka vlastností CppCoreCheck")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15,3

- Byla přidána podpora pro pravidla související se správou prostředků.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15,5

- Nové C++ základní pokyny kontrolují správnost inteligentního ukazatele, správné použití globálních inicializátorů a označení použití konstrukcí, jako je `goto` a špatné přetypování.

- Některá čísla upozornění, která najdete v 15.3, už nejsou k dispozici v 15.5. Tato upozornění byla nahrazena specifičtějšími kontrolami.

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 verze 15,6

- Přidání podpory pro analýzu jednoho souboru a vylepšení výkonu analýzy za běhu. Další informace najdete v tématu [ C++ vylepšení statických analýz pro Visual Studio 2017 15,6 Preview 2.](https://devblogs.microsoft.com/cppblog/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/)

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15,7

- Byla přidána podpora pro [/analyze: RuleSet](../build/reference/analyze-code-analysis.md), která umožňuje určit pravidla analýzy kódu, která se mají spustit.
- Přidala se podpora C++ pro další pravidla základní směrnice.  Další informace najdete v tématu [použití C++ hlavních pokynů pro kontrolu](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

## <a name="unit-testing"></a>Testování jednotek

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15,5

Google test adaptér a zvýšení. adaptér testu je nyní k dispozici jako komponenty **vývoje plochy s C++**  úlohou a jsou integrovány v **Průzkumníku testů**. Pro projekty cmake (pomocí otevřené složky) se přidala podpora CTest, i když plná integrace s **průzkumníkem testů** ještě není dostupná. Další informace naleznete v tématu [zápis testů jednotek pro C/C++](/visualstudio/test/writing-unit-tests-for-c-cpp).

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 verze 15,6

- Byla přidána podpora pro zvýšení úrovně. otestujte podporu dynamické knihovny.
- V integrovaném vývojovém prostředí je teď dostupná Šablona položky pro zvýšení. testování.

Další informace najdete v tématu [zvýšení úrovně testování testovací jednotky: dynamická podpora knihoven a nová šablona položky](https://devblogs.microsoft.com/cppblog/boost-test-unit-testing-dynamic-library-support-and-new-item-template/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15,7

[](/visualstudio/ide/find-code-changes-and-other-history-with-codelens) Byla přidána podpora CodeLens C++ pro projekty testování částí. Další informace najdete v tématu [oznámení CodeLens pro C++ testování částí](https://devblogs.microsoft.com/cppblog/announcing-codelens-for-c-unit-testing/).

## <a name="visual-studio-graphics-diagnostics"></a>Diagnostika grafiky sady Visual Studio

Visual Studio Diagnostika grafiky je sada nástrojů pro zaznamenávání a analýzu potíží s vykreslováním a výkonem v aplikacích Direct3D. Funkce Diagnostika grafiky se dají používat s aplikacemi, které běží místně na počítači s Windows, v emulátoru zařízení s Windows nebo na vzdáleném počítači nebo zařízení.

- **Vstupní & výstup pro shadery vrcholů a geometrie:** Možnost zobrazit vstup a výstup funkcí vertex shader a geometrie shaderu byla jednou z nejvíce požadovaných funkcí a teď je v nástrojích podporovaná. Jednoduše výběrem fáze VS nebo GS v zobrazení fáze zřetězení spustíte kontrolu jeho vstupu a výstupu v následující tabulce.

  ![Vstup/výstup pro shadery](media/io-shaders.png)

- **Hledání a filtrování v tabulce objektů:** Poskytuje rychlý a snadný způsob, jak najít prostředky, které hledáte.

  ![Hledat](media/search.png)

- **Historie prostředků:** Toto nové zobrazení nabízí zjednodušený způsob, jak zobrazit celou historii změn prostředku, jak bylo použito při vykreslování zachyceného snímku. Pokud chcete vyvolat historii pro libovolný prostředek, jednoduše klikněte na ikonu hodiny vedle libovolného hypertextového odkazu prostředku.

  ![Historie prostředků](media/resource-history.png)

  Tím se zobrazí nový panel nástrojů **historie prostředků** , který se vyplní historií změn prostředku.

  ![Změna historie prostředků](media/resource-history-change.png)

  Pokud byl váš rámec zachycen s povoleným zachytáváním zásobníku volání (**Nástroje sady Visual Studio > > možnosti** v části **Diagnostika grafiky**), pak je možné kontext každé události změny rychle odvodit a zkontrolovat v rámci projektu sady Visual Studio.

- **Statistika rozhraní API:** Podívejte se na Přehled využití rozhraní API ve vašem snímku na nejvyšší úrovni. Je to užitečné pro zjišťování volání, která vám nemůžete dělat vůbec, nebo volání, která provádíte příliš mnoho. Toto okno je k dispozici prostřednictvím **zobrazení > statistiky rozhraní API** v analyzátor grafiky sady Visual Studio.

  ![Statistika rozhraní API](media/api-stats.png)

- **Statistika paměti:** Zobrazení velikosti paměti, kterou ovladač přiděluje pro prostředky, které vytvoříte v rámci tohoto rámce. Toto okno je k dispozici prostřednictvím **zobrazení > statistiky paměti** v **analyzátor grafiky sady Visual Studio**. Data je možné zkopírovat do souboru CSV pro zobrazení v tabulce tak, že kliknete pravým tlačítkem a zvolíte **Kopírovat vše**.

  ![Statistiky paměti](media/memory-stats.png)

- **Ověření snímku:** Seznam nových chyb a upozornění nabízí snadný způsob, jak procházet seznam událostí na základě potenciálních problémů zjištěných ladicí vrstvou Direct3D. Kliknutím na **zobrazit > ověření rámce** v analyzátor grafiky sady Visual Studio otevřete okno. Pak kliknutím na **Spustit ověření** spusťte analýzu. Dokončení může trvat několik minut, v závislosti na složitosti snímku.

  ![Ověření snímku](media/frame-validation.png)

- **Analýza snímků pro D3D12:** Pomocí analýzy snímků můžete analyzovat výkon volání při volání s použitím pořízených experimentů "Co je if". Přepněte na kartu analýza snímků a spusťte analýzu pro zobrazení sestavy. Další podrobnosti najdete na [GoingNative 25: Visual Studio Analýza grafických snímků](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) video.

  ![Analýza snímků](media/frame-analysis.png)

- **Vylepšení využití GPU:** Pomocí nástroje Profiler využití GPU sady Visual Studio můžete otevřít trasování pomocí zobrazení GPU nebo nástroje Windows Performance Analyzer (WPA), kde najdete podrobnější analýzu. Pokud máte sadu Windows Performance Toolkit nainstalovanou, existují dva hypertextové odkazy, jeden pro WPA a druhý pro zobrazení GPU, a to v pravém dolním rohu přehledu relace.

  ![Využití GPU](media/gpu-usage.png)

  Trasování otevřená v zobrazení GPU prostřednictvím tohoto odkazu podporují synchronizaci přiblížení a posouvání na časové ose mezi zobrazením VS a GPU. Zaškrtávací políčko v sadě VS slouží k řízení, zda je synchronizace povolena nebo nikoli.

  ![Zobrazení GPU](media/gpu-view.png)

::: moniker-end

::: moniker range="=vs-2015"

Úplný seznam toho, co je nového v rámci sady Visual Studio 2015 Update 3, najdete v článku [ C++ co je nového 2003 až 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015). Další informace o tom, co je nového ve všech sadách Visual Studio 2015, najdete v poznámkách k verzi propojených z historie zpráv k [vydání verzí sady Visual studio 2015](/visualstudio/releasenotes/vs2015-version-history). Informace o tom, co je nového C++ v aplikaci visual Studio 2019, najdete v tématu [co C++ je nového v aplikaci Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019). Informace o tom, co je nového C++ v aplikaci visual Studio 2017, najdete v tématu [novinky C++ v aplikaci Visual Studio 2017](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017).

::: moniker-end
