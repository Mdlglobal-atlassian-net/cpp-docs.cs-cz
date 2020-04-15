---
title: Novinky v jazyce C++ v sadě Visual Studio
ms.date: 07/02/2019
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
ms.openlocfilehash: 9b656d4e13fe241c22a9c555d1c597016c5353d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366821"
---
# <a name="whats-new-for-c-in-visual-studio"></a>Novinky v jazyce C++ v sadě Visual Studio

::: moniker range=">=vs-2019"

Visual Studio 2019 přináší mnoho aktualizací a oprav do prostředí Microsoft C++. Opravili jsme mnoho chyb a problémů v kompilátoru a nástrojích. Mnoho z těchto problémů bylo odesláno zákazníky prostřednictvím [nahlášení problému](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019) a poskytnutí možností [návrhu](https://developercommunity.visualstudio.com/spaces/62/index.html) v části **Odeslat zpětnou vazbu**. Děkujeme vám, že hlásíte chyby! Další informace o novince ve všech Visual Studiu najdete na stránce [Co je nového ve Visual Studiu 2019](/visualstudio/ide/whats-new-visual-studio-2019). Informace o tom, co je nového pro C++ ve Visual Studiu 2017, najdete v tématu [Co je nového pro C++ ve Visual Studiu 2017](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017). Informace o novince pro C++ ve Visual Studiu 2015 a starších verzích najdete v [tématu Visual C++ What's New 2003 až 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="c-compiler"></a>kompilátor C++

- Vylepšená podpora funkcí a oprav oprav jazyka C++17 a experimentální podpora funkcí jazyka C++20, jako jsou moduly a korutiny. Podrobné informace naleznete v tématu [C++ Vylepšení shody v sadě Visual Studio 2019](cpp-conformance-improvements.md).

- Možnost `/std:c++latest` nyní obsahuje funkce jazyka C++20, které nemusí být nutně dokončeny, \<včetně počáteční podpory pro operátora C++20 => ("kosmická loď") pro třícestné porovnání.

- Přepínač `/Gm` kompilátoru Jazyka C++ je nyní zastaralé. Zvažte zakázání přepínače ve `/Gm` skriptech sestavení, pokud je explicitně definován. Můžete však také bezpečně ignorovat upozornění `/Gm`na vyřazení , protože není považováno za chybu při`/WX`použití "Považovat varování za chyby" ( ).

- Jako MSVC začíná implementaci funkcí z C ++ 20 `/std:c++latest` standardní pracovní verze `/clr` pod příznakem, `/std:c++latest` `/Gm`je nyní nekompatibilní s (všechny příchutě), `/ZW`a . V Visual Studio 2019 `/std:c++17` použití nebo `/std:c++14` režimy při kompilaci s `/clr`, `/ZW`, nebo `/Gm` (ale viz předchozí odrážka).

- U aplikací C++ pro konzoly a klasickou pracovní plochu se už negenerují předkompilované hlavičky.

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, zabezpečení, diagnostika a správa verzí

Vylepšená `/Qspectre` analýza s pro poskytování pomoci zmírnění pro Spectre varianta 1 (CVE-2017-5753). Další informace naleznete [v tématu Spectre Mitigations in MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).

## <a name="c-standard-library-improvements"></a>Vylepšení standardní knihovny C++

- Implementace dalších funkcí knihovny C++17 a C++20 a oprav správnosti. Podrobné informace naleznete v tématu [C++ Vylepšení shody v sadě Visual Studio 2019](cpp-conformance-improvements.md).

- Clang-Format byl použit na hlavičky standardní knihovny C++ pro lepší čitelnost.

- Vzhledem k tomu, že Visual Studio nyní podporuje pouze můj kód pro `std::function` `std::visit` C++, standardní knihovna již není třeba poskytovat vlastní strojní zařízení pro a dosáhnout stejného efektu. Odstranění tohoto strojního zařízení nemá do značné míry žádné uživatelem viditelné účinky. Jedinou výjimkou je, že kompilátor již nebude vyrábět diagnostiku, která označuje problémy na řádku 15732480 nebo 16707566 \<type_traits> nebo \<> variant.

## <a name="performancethroughput-improvements-in-the-compiler-and-standard-library"></a>Vylepšení výkonu a propustnosti kompilátoru a standardní knihovny

- Sestavení vylepšení propustnost, včetně způsobu propojení zpracovává vstupně-v.o a čas propojení v typu PDB sloučení a vytváření.

- Přidána základní podpora pro vektorizaci OpenMP SIMD. Můžete jej povolit pomocí nového přepínače kompilátoru `-openmp:experimental`. Tato volba umožňuje, aby smyčky `#pragma omp simd` s anotací mohly být vektorizovány. Vektorizace není zaručena a smyčky anotované, ale ne vektorizované, dostanou upozornění. Nejsou podporovány žádné klauzule SIMD; jsou ignorovány a je nahlášeno varování.

- Byl přidán nový přepínač `-Ob3`příkazového řádku , což `-Ob2`je agresivnější verze aplikace . `-O2`(optimalizovat binární pro rychlost) `-Ob2` stále znamená ve výchozím nastavení. Pokud zjistíte, že kompilátor není dostatečně agresivně, `-O2 -Ob3`zvažte předání .

- Pro podporu ruční vektorizace smyček s voláním funkcí matematické knihovny a některých dalších operací, jako je dělení celého čísla, jsme přidali podporu pro vnitřní funkce Short Vector Math Library (SVML). Tyto funkce vypočítat 128bitové, 256bitové nebo 512bitové vektorové ekvivalenty. Definice podporovaných funkcí najdete v příručce [Intel Intrinsic Guide](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML).

- Nové a vylepšené optimalizace:

  - Konstantní skládání a aritmetické zjednodušení pro výrazy pomocí vektorových vnitřních součástí SIMD pro plovoucí i celočíselné formuláře.

  - Výkonnější analýza pro extrahování informací z řídicího toku (příkazy if/else/switch) k odstranění větví se vždy ukázala jako pravdivá nebo nepravdivá.

  - Vylepšené memset unrolling používat SSE2 vektorové instrukce.

  - Vylepšené odstranění zbytečných kopií struktury/třídy, zejména pro programy jazyka C++, které procházejí hodnotou.

  - Vylepšená optimalizace `memmove`kódu `std::copy` pomocí `std::vector` `std::string` , například nebo a konstrukce.

- Optimalizovala standardní fyzický návrh knihovny, aby se zabránilo kompilaci částí standardní knihovny, které nejsou přímo zahrnuty. Tato změna zkrátit dobu sestavení prázdný soubor, který obsahuje pouze \<vektorové> na polovinu. V důsledku toho může být `#include` nutné přidat direktivy pro záhlaví, které byly dříve nepřímo zahrnuty. Například kód, `std::out_of_range` který používá nyní `#include <stdexcept>`může být nutné přidat . Kód, který používá operátor vložení datového `#include <ostream>`proudu, může nyní potřebovat přidat . Výhodou je, že pouze \<překladové jednotky, \<které skutečně používají stdexcept> nebo ostream> součásti, platí náklady na propustnost za jejich kompilaci.

- `if constexpr`byla použita na více místech ve standardní knihovně pro lepší propustnost a sníženou velikost kódu v operacích kopírování, v permutacích, jako je reverzní a rotace, a v knihovně paralelních algoritmů.

- Standardní knihovna nyní `if constexpr` interně používá ke snížení doby kompilace, a to i v režimu C ++ 14.

- Detekce dynamického propojení za běhu pro knihovnu paralelních algoritmů již nepoužívá celou stránku k uložení pole ukazatele funkce. Označení této paměti jen pro čtení již nebylo považováno za relevantní pro účely zabezpečení.

- `std::thread`Konstruktor společnosti 's již nečeká na spuštění vlákna a již nevloží tolik vrstev `_beginthreadex` volání funkce mezi základní knihovnu C a dodaný volatelný objekt. Dříve `std::thread` dal 6 `_beginthreadex` funkcí mezi a dodávané callable objektu, který byl `std::invoke`snížen pouze na 3 (2 z nich jsou jen ). Tato změna také řeší chyby obskurní časování, kde `std::thread` by zavěsil konstruktor, pokud by se systémové hodiny změnily přesně v okamžiku, kdy `std::thread` byla vytvořena.

- Opravena regrese výkonu `std::hash` v tom, kterou `std::hash<std::filesystem::path>`jsme zavedli při implementaci .

- Standardní knihovna nyní používá destruktory namísto catch bloků na několika místech k dosažení správnosti. Tato změna má za následek lepší interakci ladicího programu: Výjimky, které vyvoláte prostřednictvím standardní knihovny v ohrožených umístěních, se nyní zobrazují jako vyvoláné z původního webu vyvolání, nikoli jako naše opětovné vyvolání. Ne všechny standardní bloky zachycení knihovny byly odstraněny; očekáváme, že počet bloků úlovků bude snížen v pozdějších verzích MSVC.

- Suboptimální codegen `std::bitset` v způsobené podmíněné throw uvnitř noexcept funkce byla opravena faktoring mimo vyvolání cesty.

- A `std::list` `std::unordered_*` rodina používat non-ladění iterátory interně na více místech.

- Několik `std::list` členů byly změněny na opětovné použití uzlu seznamu, kde je to možné, spíše než jejich zrušení a přerozdělení. Například vzhledem `list<int>` k tomu, že již má `assign(4, 1729)` velikost 3, volání nyní přepíše ints v prvních uzlech seznamu 3 a přidělí jeden nový uzel seznamu s hodnotou 1729.

- Všechna standardní volání `erase(begin(), end())` knihovny `clear()`byla změněna na .

- `std::vector`nyní inicializuje a vymazává prvky efektivněji v určitých případech.

- Vylepšení, `std::variant` aby byl optimalizován, což vede k lépe generovanému kódu. Vkládání kódu je nyní `std::visit`mnohem lepší s .

## <a name="c-ide"></a>C++ IDE

### <a name="live-share-c-support"></a>Podpora pro Live Share C++

[Live Share](/visualstudio/liveshare/) teď podporuje C++, což umožňuje vývojářům pomocí Sady Visual Studio nebo Visual Studio Code spolupracovat v reálném čase. Další informace naleznete [v tématu Oznámení živého sdílení pro C++: Sdílení a spolupráce v reálném čase](https://devblogs.microsoft.com/cppblog/cppliveshare/)

### <a name="intellicode-for-c"></a>IntelliCode pro C++

##### <a name="visual-studio-2019-version-161"></a> Visual Studio 2019 verze 16.1

IntelliCode je volitelné rozšíření, které používá vlastní rozsáhlé školení a kontext kódu, aby to, co s největší pravděpodobností použít v horní části seznamu dokončení. To může často eliminovat potřebu procházet seznamem dolů. Pro C++ IntelliCode nabízí nejvíce nápovědy při použití oblíbených knihoven, jako je například standardní knihovna. Je k dispozici jako součást pracovního vytížení v instalačním programu. Další informace naleznete [v tématu Návrhy na dokončení ai-assisted code come to C++ via IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/).

### <a name="template-intellisense"></a>Šablona IntelliSense

**Panel šablony** nyní používá uživatelské **okno náhledu** spíše než modální okno, podporuje vnořené šablony a předem vyplní všechny výchozí argumenty do **okna náhledu**. Další informace najdete [v tématu Šablona IntelliSense Vylepšení pro Visual Studio 2019 Náhled 2](https://devblogs.microsoft.com/cppblog/template-intellisense-improvements-for-visual-studio-2019-preview-2/). Naposledy **použitý** rozbalovací seznam na **panelu šablon** umožňuje rychlé přepínání mezi předchozími sadami ukázkových argumentů.

### <a name="new-start-window-experience"></a>Nové prostředí úvodního okna

Při spouštění ide se zobrazí nové okno Start s možnostmi otevření nedávných projektů, klonování kódu ze správy zdrojového kódu, otevření místního kódu jako řešení nebo složky nebo vytvoření nového projektu. Dialogové okno Nový projekt bylo také přepracováno na filtrovatelné prostředí pro vyhledávání.

### <a name="new-names-for-some-project-templates"></a>Nové názvy pro některé šablony projektů

Upravili jsme několik názvů a popisů šablon projektu tak, aby odpovídaly aktualizovanému dialogovému oknu Nový projekt.

### <a name="various-productivity-improvements"></a>Různá zlepšení produktivity

Visual Studio 2019 obsahuje následující funkce, které vám pomohou usnadnit a intuitivnější kódování:

- Rychlé opravy pro:
  - Přidat chybějící #include
  - NULL pro nullptr
  - Přidat chybějící středník
  - Překlad chybějícího oboru názvů nebo oboru
  - Nahradit špatné indirection operandy (chcete-li\* & a & ) \*
- Rychlé informace pro blok najetím na uzavírací složenou závorku
- Náhled záhlaví / soubor kódu
- Přejít na definici v #include otevře soubor

Další informace najdete [v tématu C++ Zvýšení produktivity ve Visual Studiu 2019 Náhled 2](https://devblogs.microsoft.com/cppblog/c-productivity-improvements-in-visual-studio-2019-preview-2/).

### <a name="quickinfo-improvements"></a>Vylepšení rychlých informací

##### <a name="visual-studio-2019-version-161"></a> Visual Studio 2019 verze 16.1

Popisek Rychlý přehled nyní respektuje sémantické zbarvení editoru. Má také nový odkaz **Search Online,** který bude vyhledávat online dokumenty, aby se dozvěděl více o konstrukci hovered code. U kódu s červeným imggled bude odkaz poskytnutý rychlými informacemi hledat chybu online. Tímto způsobem nemusíte znovu zadávat zprávu do prohlížeče. Další informace najdete [v tématu Vylepšení rychlých informací ve Visual Studiu 2019: Kolovat a hledání online](https://devblogs.microsoft.com/cppblog/quick-info-improvements-in-visual-studio-2019-colorization-and-search-online/).

### <a name="intellicode-available-in-c-workload"></a>IntelliCode je k dispozici v zatížení C++

##### <a name="visual-studio-2019-version-161"></a> Visual Studio 2019 verze 16.1

IntelliCode se nyní dodává jako volitelná součást ve vývoji plochy s úlohami **Jazyka C++.** Další informace najdete [v tématu Vylepšená C++ IntelliCode nyní dodává s Visual Studio 2019](https://devblogs.microsoft.com/cppblog/improved-c-intellicode-now-ships-with-visual-studio-2019/).

## <a name="cmake-support"></a>Podpora pro CMake

- Podpora pro CMake 3.14

- Visual Studio teď můžete otevřít existující CMake mezipaměti generované externínástroje, jako je například CMakeGUI, přizpůsobené meta-sestavení systémů nebo vytvářet skripty, které vyvolávají cmake.exe sami.

- Vylepšený výkon technologie IntelliSense.

- Nový editor nastavení poskytuje alternativu k ruční úpravě souboru CMakeSettings.json a poskytuje některé parity s CMakeGUI.

- Visual Studio vám pomůže rozběhnout vývoj v jazyce C++ s nástroji CMake na Linuxu díky rozpoznání, jestli máte na počítači s Linuxem kompatibilní verzi CMake. Pokud ne, aplikace vám nabídne její instalaci.

- Nekompatibilní nastavení v CMakeSettings, jako je například neshodné architektury nebo nekompatibilní nastavení generátoru CMake, zobrazit vlnovky v editoru JSON a chyby v seznamu chyb.

- Po spuštění příkazu `vcpkg integrate install` se automaticky rozpozná sada nástrojů vcpkg a povolí se pro projekty CMake, které jsou otevřené v integrovaném vývojovém prostředí. Toto chování můžete vypnout tak, že v nástroji CMakeSettings zadáte prázdný soubor sady nástrojů.

- Projekty CMake teď ve výchozím nastavení aktivují ladění s možností Pouze můj kód.

- Upozornění statické analýzy u projektů CMake teď můžete zpracovat na pozadí a zobrazit v editoru.

- Jasnější sestavení a konfigurace zpráv "begin" a 'end' pro projekty CMake a podporu pro událo v průběhu sestavení sady Visual Studio. Navíc je nyní CMake podrobnost nastavení v **nástrojích > možnosti** přizpůsobit úroveň podrobností CMake sestavení a konfigurační zprávy ve výstupním okně.

- Nastavení `cmakeToolchain` je nyní podporováno v souboru CMakeSettings.json pro určení řetězů nástrojů bez ruční úpravy příkazového řádku CMake.

- Nová **zkratka** nabídky Build All **Ctrl+Shift+B**.

##### <a name="visual-studio-2019-version-161"></a> Visual Studio 2019 verze 16.1

- Integrovaná podpora pro úpravy, vytváření a ladění projektů CMake s Clang/LLVM. Další informace naleznete [v tématu Clang/LLVM Support in Visual Studio](https://devblogs.microsoft.com/cppblog/clang-llvm-support-in-visual-studio/).

## <a name="linux-and-the-windows-subsystem-for-linux"></a>Linux a Podsystém Windows pro Linux

##### <a name="visual-studio-2019-version-161"></a> Visual Studio 2019 verze 16.1

- Podpora pro [AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) v Linuxu a CMake multiplatformních projektech. Další informace naleznete [v tématu AddressSanitizer (ASan) pro linuxové úlohy ve Visual Studiu 2019](https://devblogs.microsoft.com/cppblog/addresssanitizer-asan-for-the-linux-workload-in-visual-studio-2019/).

- Integrovaná podpora Visual Studia pro použití jazyka C++ se systémem Windows Subsystem for Linux (WSL). Další informace naleznete v tématu [C++ s Visual Studio 2019 a Windows Subsystem pro Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

## <a name="incredibuild-integration"></a>Integrace IncrediBuild

IncrediBuild je součástí jako volitelná součást ve vývoji plochy s úlohou **C++.** Monitor sestavení sestavení sestavení IncrediBuild je plně integrován do integrovaného prostředí Visual Studio. Další informace naleznete [v tématu Vizualizace sestavení pomocí sledování sestavení IncrediBuild a Visual Studio 2019](https://devblogs.microsoft.com/cppblog/visualize-your-build-with-incredibuilds-build-monitor-and-visual-studio-2019/).

## <a name="debugging"></a>Ladění

- Pro aplikace jazyka C++ spuštěné v systému Windows se soubory PDB nyní načítají v samostatném 64bitovém procesu. Tato změna řeší řadu selhání způsobených ladicí program nedostatek paměti při ladění aplikací, které obsahují velký počet modulů a souborů PDB.

- Hledání je povoleno v oknech **Sledovat**, **Autos**a **Locals.**

## <a name="windows-desktop-development-with-c"></a>Vývoj plochy windows s C++

- Tito průvodci knihovnou ATL/MFC jazyka C++ již nejsou k dispozici:

  - Průvodce komponentami ATL COM+ 1.0
  - Průvodce součástí Aktivní serverové stránky serveru ATL
  - Průvodce zprostředkovatelem ATL OLE DB
  - Průvodce stránkou vlastností ATL
  - Průvodce příjemcem ATL OLE DB
  - Příjemce rozhraní MFC ODBC
  - Třída MFC z ovládacího prvku ActiveX
  - Třída MFC z typu Lib.

  Ukázkový kód pro tyto technologie je archivován v Microsoft Docs a v úložišti GitHub VCSamples.

- V instalačním programu sady Visual Studio už není dostupná sada Windows 8.1 SDK. Doporučujeme upgradovat projekty c++ na nejnovější windows 10 SDK. Pokud někde používáte pevnou závislost na sadě Windows 8.1 SDK, můžete si ji stáhnout z archivu sad Windows SDK.

- V nejnovější sadě nástrojů C++ už nebude k dispozici cílení na Windows XP. Cílení na XP pomocí překladače MSVC na úrovni VS 2017 & knihovny jsou stále podporovány a lze je instalovat prostřednictvím "Jednotlivých komponent".

- Naše dokumentace aktivně odrazuje od používání slučovacích modulů k nasazení modulu Runtime Visual C++. Děláme další krok této vydání označení našich MSMs jako zastaralé. Zvažte migraci centrálního nasazení VCRuntime z balíčků MSM na balíček opětovné distribuce.

## <a name="mobile-development-with-c-android-and-ios"></a>Vývoj mobilních zařízení s C++ (Android a iOS)

Výchozím prostředím C++ Android je nyní Android SDK 25 a Android NDK 16b.

## <a name="clangc2-platform-toolset"></a>Sada nástrojů platformy Clang/C2

Experimentální složka Clang/C2 byla odstraněna. Sadu nástrojů MSVC použijte pro úplnou shodu standardů Jazyka C++ s `/permissive-` programem a `/std:c++17`, nebo řetězec nástrojů Clang/LLVM pro systém Windows.

## <a name="code-analysis"></a>Analýza kódu

- Analýza kódu se teď spouští automaticky na pozadí. Upozornění se v editoru během psaní podtrhávají zelenou vlnovkou. Další informace najdete [v tématu Analýza kódu editoru v Visual Studiu 2019 Preview 2](https://devblogs.microsoft.com/cppblog/in-editor-code-analysis-in-visual-studio-2019-preview-2/).

- Nová experimentální pravidla ConcurrencyCheck pro známé typy \<standardní knihovny z hlavičky mutex>. Další informace naleznete [v tématu Analýza kódu souběžnosti v sadě Visual Studio 2019](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/).

- Aktualizovaná částečná implementace [kontroly profilu Životnost](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/), která detekuje visící ukazatele a odkazy. Další informace najdete [v tématu Aktualizace celoživotního profilu ve Visual Studiu 2019 Preview 2](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/).

- Další kontroly související s korutinou, včetně C26138, C26810, C26811 a experimentálního pravidla C26800. Další informace naleznete [v tématu New Code Analysis Checks in Visual Studio 2019: use-after-move and coroutine](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/).

##### <a name="visual-studio-2019-version-161"></a> Visual Studio 2019 verze 16.1

- Nové rychlé opravy pro neinicializované kontroly proměnných. Další informace naleznete [v tématu Nové rychlé opravy analýzy kódu pro neinicializovanou paměť (C6001) a použití před init (C26494) upozornění](https://devblogs.microsoft.com/cppblog/new-code-analysis-quick-fixes-for-uninitialized-memory-c6001-and-use-before-init-c26494-warnings/).

## <a name="unit-testing"></a>Testování jednotek

Šablona spravovaného testovacího projektu C++ už není dostupná. Můžete pokračovat v používání spravované ho c++ testovací ho frameworku v existujících projektech. Pro nové testy částí zvažte použití jednoho z nativních testovacích architektur, pro které Visual Studio poskytuje šablony (MSTest, Google Test) nebo šablonu spravovaného testovacího projektu C#.

::: moniker-end

::: moniker range="=vs-2017"

Visual Studio 2017 přináší mnoho aktualizací a oprav do prostředí C++. Opravili jsme více než 250 chyb a nahlásili problémy v kompilátoru a nástrojích, mnoho z nich odeslaných zákazníky prostřednictvím [nahlášení problému a poskytnutí](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2017) možností návrhu v části **Odeslat zpětnou vazbu**. Děkujeme vám, že hlásíte chyby! Další informace o novince ve všech Visual Studio najdete v tématu [Co je nového v Sadě Visual Studio 2017](/visualstudio/ide/whats-new-visual-studio-2017?view=vs-2017). Informace o tom, co je nového pro C++ ve Visual Studiu 2019, najdete v [tématu Co je nového pro C++ ve Visual Studiu](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019). Informace o novince pro C++ ve Visual Studiu 2015 a starších verzích najdete v [tématu Visual C++ What's New 2003 až 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="c-compiler"></a>kompilátor C++

### <a name="c-conformance-improvements"></a>Vylepšení shody c++

V této verzi jsme kompilátor jazyka C++ a standardní knihovny doplnili rozšířenou podporou pro funkce C++11 a C++14, a také předběžnou podporou pro některé funkce očekávané ve standardu C++17. Podrobné informace naleznete v tématu [C++ Vylepšení shody v sadě Visual Studio 2017](cpp-conformance-improvements.md).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

Kompilátor podporuje přibližně 75 % funkcí, které jsou nové v jazyce `constexpr` C++17, včetně strukturovaných vazeb, lambdů, `if constexpr`vložkových proměnných, výrazů přeložení a přidání `noexcept` do systému typů. Tyto funkce jsou k dispozici v rámci možnosti **/std:c++17.** Další informace najdete v tématu [Vylepšení shody jazyka C++ v sadě Visual Studio 2017](cpp-conformance-improvements.md)

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

Sada nástrojů kompilátoru MSVC ve visual tašti ve verzi 15.7 nyní odpovídá standardu C++. Další informace naleznete [v tématu Oznámení: MSVC odpovídá standardu C++](https://devblogs.microsoft.com/cppblog/announcing-msvc-conforms-to-the-c-standard/) a [shody jazyka Microsoft C++](../visual-cpp-language-conformance.md).

##### <a name="visual-studio-2017-version-158"></a>Visual Studio 2017 verze 15.8

Přepínač kompilátoru [/experimental:preprocessor](../build/reference/experimental-preprocessor.md) umožňuje nový experimentální preprocesor MSVC, který bude nakonec v souladu se všemi platnými standardy C a C++. Další informace naleznete v [přehledu experimentálních preprocesorů MSVC](../preprocessor/preprocessor-experimental-overview.md).

### <a name="new-compiler-options"></a>Nové možnosti kompilátoru

- [/tolerantní-](../build/reference/permissive-standards-conformance.md): Povolte všechny možnosti kompilátoru shody přísných standardů a `__declspec(dllimport)`zakažte většinu rozšíření kompilátoru specifických pro microsoft (ale ne například). Tato možnost je ve výchozím nastavení zapnutá ve Visual Studiu 2017 verze 15.5.  Režim **/permissive-** conformance zahrnuje podporu pro vyhledávání dvoufázového názvu. Další informace naleznete v tématu [C++ Vylepšení shody v sadě Visual Studio](cpp-conformance-improvements.md).

- [/diagnostics](../build/reference/diagnostics-compiler-diagnostic-options.md): Povolit zobrazení čísla řádku, čísla řádku a sloupce nebo čísla řádku a sloupce a stříšky pod řádkem kódu, kde byla nalezena diagnostická chyba nebo upozornění.

- [/debug:fastlink](../build/reference/debug-generate-debug-info.md): Povolte až o 30 % rychlejší přírůstkové časy propojení (vs. Visual Studio 2015) tím, že nezkopírujete všechny informace o ladění do souboru PDB. Soubor PDB místo toho odkazuje na informace o ladění pro objekt a soubory knihovny použité k vytvoření spustitelného souboru. Viz [Rychlejší c++ cyklus sestavení ve VS "15" s /Debug:fastlink](https://devblogs.microsoft.com/cppblog/faster-c-build-cycle-in-vs-15-with-debugfastlink/) a [doporučení k urychlení sestavení C++ v sadě Visual Studio](https://devblogs.microsoft.com/cppblog/recommendations-to-speed-c-builds-in-visual-studio/).

- Visual Studio 2017 umožňuje použití [/sdl](../build/reference/sdl-enable-additional-security-checks.md) s [/await](../build/reference/await-enable-coroutine-support.md). Odebrali jsme [/RTC](../build/reference/rtc-run-time-error-checks.md) omezení s Coroutines.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

- [/std:c++14 a /std:c++latest](../build/reference/std-specify-language-standard-version.md): Tyto možnosti kompilátoru umožňují přihlásit se k určitým verzím programovacího jazyka ISO C++ v projektu. Většina nových standardních funkcí konceptu je chráněna možností **/std:c++latest.**

- [/std:c++17](../build/reference/std-specify-language-standard-version.md) umožňuje sadu funkcí jazyka C++17 implementovaných kompilátorem. Tato možnost zakáže kompilátor a standardní knihovnu podporu pro funkce, které jsou změněny nebo nové ve verzích pracovní koncept a defekt aktualizace standardu C++ po C ++ 17. Chcete-li tyto funkce povolit, použijte **parametr /std:c++latest**.

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, zabezpečení, diagnostika a správa verzí

Tato verze přináší několik vylepšení v optimalizaci, generování kódu, správu verzí sady nástrojů a diagnostiky. Mezi důležitá vylepšení patří:

- Vylepšené generování kódu smyček: Podpora automatické vektorizace dělení konstantních celých čísel, lepší identifikace vzorů memset
- Vylepšené zabezpečení kódu: Vylepšené emise diagnostiky překladače přetečení vyrovnávací paměti a [/guard:cf](../build/reference/guard-enable-control-flow-guard.md) nyní chrání příkazy přepínače, které generují tabulky odkazů.
- Správa verzí: Hodnota integrovaného preprocesorového makra ** \_MSC\_VER** se nyní monotonicky aktualizuje při každé aktualizaci sady nástrojů Visual C++. Další informace naleznete v [tématu Visual C++ Compiler Version](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/).
- Nové rozložení sady nástrojů: Kompilátor a související nástroje sestavení mají nové umístění a adresářovou strukturu ve vývojovém počítači. Nové rozložení umožňuje souběžné instalace více verzí kompilátoru. Další informace naleznete [v tématu Compiler Tools Layout in Visual Studio 2017](https://devblogs.microsoft.com/cppblog/compiler-tools-layout-in-visual-studio-15/).
- Vylepšená diagnostika: Ve výstupním okně se nyní zobrazuje sloupec, ve kterém dojde k chybě. Další informace naleznete v [tématu C++ vylepšení diagnostiky kompilátoru v VS "15" Náhled 5](https://devblogs.microsoft.com/cppblog/c-compiler-diagnostics-improvements-in-vs-15-rc/).
- Při použití co-rutiny, experimentální klíčové slovo **výnos** (k dispozici pod **/await** možnost) byla odebrána. Váš kód by měl `co_yield` být aktualizován tak, aby místo toho používal. Další informace naleznete v [ `yield` tématu klíčové slovo, které `co_yield` se má stát ve VS 2017](https://devblogs.microsoft.com/cppblog/yield-keyword-to-become-co_yield-in-vs-2017/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

Další vylepšení diagnostiky v kompilátoru. Další informace naleznete [v tématu Diagnostic Improvements in Visual Studio 2017 15.3.0](https://devblogs.microsoft.com/cppblog/diagnostic-improvements-in-vs2017-15-3-0/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

Výkon za běhu Visual C++ se stále zlepšuje díky lepší kvalitě generovaného kódu. Teď stačí překompilovat kód a vaše aplikace běží rychleji. Některé optimalizace kompilátoru jsou zcela nové, jako je například vektorizace `sin(x)` podmíněných skalárních úložišť, kombinování volání a `cos(x)` do nového `sincos(x)`a eliminace redundantních instrukcí z optimalizátoru SSA. Další optimalizace kompilátoru jsou vylepšení existujících funkcí, jako je například vectorizer heuristiky pro podmíněné výrazy, lepší optimalizace smyčky a plovoucí min/max codegen. Propojovací systém má novou a rychlejší **implementaci /OPT:ICF,** což může mít za následek až 9 % zrychlení doby propojení a další opravy perf v přírůstkovém propojení. Další informace naleznete [v tématech /OPT (Optimalizace)](../build/reference/opt-optimizations.md) a [/INCREMENTAL (Postupně link)](../build/reference/incremental-link-incrementally.md).

Kompilátor Microsoft C++ podporuje AVX-512 společnosti Intel, včetně pokynů pro délku vektoru, které přinášejí nové funkce v registrech AVX-512 do 128bitových a 256bitových registrů.

Možnost [/Zc:noexceptTypes-](../build/reference/zc-noexcepttypes.md) lze použít k návratu k verzi Jazyka `noexcept` C++14 při použití režimu C++17 obecně. Tato možnost umožňuje aktualizovat zdrojový kód tak, aby odpovídal c++ 17 bez nutnosti přepisovat veškerý `throw()` kód současně. Další informace naleznete v [tématu Dynamické odebrání specifikace výjimky a noexcept](cpp-conformance-improvements.md#noexcept_removal).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

- Nový přepínač kompilátoru [/Qspectre,](../build/reference/qspectre.md) který pomáhá zmírnit proti spekulativním útokům na straně kanálu provádění. Další informace naleznete [v tématu Spectre skutečnosti snižující závažnost rizika v MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).
- Nové diagnostické upozornění pro zmírnění Spectre. Další informace naleznete [v tématu Diagnostika Spectre ve Visual Studiu 2017 verze 15.7 Náhled 4](https://devblogs.microsoft.com/cppblog/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/).
- Nová hodnota pro /Zc, **/Zc:__cplusplus**, umožňuje správné vykazování standardní podpory jazyka C++. Pokud je například přepínač nastaven a kompilátor je v režimu /std:c++17, hodnota se rozšíří na **201703L**. Další informace naleznete v tématu [MSVC nyní správně hlásí __cplusplus](https://devblogs.microsoft.com/cppblog/msvc-now-correctly-reports-__cplusplus/).

## <a name="c-standard-library"></a>Standardní knihovna C++

### <a name="correctness-improvements"></a>Vylepšení správnosti

##### <a name="visual-studio-2017-rtm-version-150"></a>Visual Studio 2017 RTM (verze 15.0)

- Drobná `basic_string` `_ITERATOR_DEBUG_LEVEL != 0` vylepšení diagnostiky. Přeskočení kontroly IDL v sadě řetězců teď oznámí konkrétní chování, které toto přeskočení způsobilo. Například místo zprávy oznamující, že iterátor řetězce nejde přesměrovat, se teď zobrazí zpráva s oznámením, že iterátor řetězce nejde přesměrovat, protože je mimo rozsah (např. je to koncový iterátor).
- Opraven `std::promise` operátor přiřazení přesunutí, který dříve mohl způsobit navždy zablokování kódu.
- Opraveny chyby `atomic<T*>` kompilátoru s implicitním převodem na `T*`.
- `pointer_traits<Ptr>`nyní správně `Ptr::rebind<U>`detekuje .
- Opraven chybějící `const` kvalifikátor v operátoru `move_iterator` odčítání.
- Opraven tichý chybný kódgen pro stavové uživatelem `propagate_on_container_copy_assignment` definované `propagate_on_container_move_assignment`alokátory, které požadovaly a .
- `atomic<T>`nyní toleruje přetížené `operator&()`.
- Mírně vylepšená diagnostika kompilátoru pro nesprávná `bind()` volání.

Úplný seznam vylepšení standardní knihovny ve Visual Studiu 2017 RTM najdete v tématu C++ Team Blog [položky Standardní knihovna opravy v VS 2017 RTM](https://devblogs.microsoft.com/cppblog/stl-fixes-in-vs-2017-rtm/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

- Standardní knihovna kontejnery `numeric_limits<difference_type>::max()` nyní `max()` upínají jejich `size_type` `max_size()` spíše než . Tato změna zajišťuje, že `distance()` výsledek na iterátory z tohoto kontejneru `distance()`je reprezentovatelný v návratový typ .
- Opravena chybějící `auto_ptr<void>`specializace .
- V `for_each_n()` `generate_n()`, `search_n()` a algoritmy dříve nepodařilo zkompilovat, pokud argument length nebyl integrální typ; nyní se pokoušejí převést neintegrální délky `difference_type`na iterátory.
- `normal_distribution<float>`již vydává varování uvnitř standardní knihovny o zúžení z dvojité na plovoucí.
- Opraveny `basic_string` některé `npos` operace, `max_size()` které se používaly místo při kontrole maximálního přetečení velikosti.
- `condition_variable::wait_for(lock, relative_time, predicate)`by čekat na celou relativní dobu v případě falešné probuzení. Nyní bude čekat pouze jeden interval relativního času.
- `future::get()`nyní zruší platnost `future`, jak to vyžaduje norma.
- `iterator_traits<void *>`bývala tvrdá chyba, protože se `void&`pokusila vytvořit ; nyní se čistě stává prázdnou strukturou, která umožňuje použití `iterator_traits` v podmínkách "is iterator" SFINAE.
- Některá upozornění hlášená hlavičkami Clang **-Wsystem byla opravena.**
- Opravena také "specifikace výjimky v deklaraci neodpovídá předchozí deklaraci" vykázané Clang **-Wmicrosoft-exception-spec**.
- Opravena také upozornění na řazení seznamu mem-initializer,hlášená clanga a c1XX.
- Neuspořádané kontejnery nevyměnily své funkce hash nebo predikáty, když byly kontejnery vyměněny. Teď už ano.
- Mnoho kontejnerswap operace `noexcept` jsou nyní označeny (jako naše standardní knihovna`propagate_on_container_swap` nikdy v úmyslu vyvolat výjimku při zjišťování non-equal-alokátor nedefinované chování stavu).
- Mnoho `vector<bool>` operací je `noexcept`nyní označeno .
- Standardní knihovna bude nyní vynucovat odpovídající přidělování `value_type` (v režimu C ++ 17) s únikovým poklopem pro odhlášení.
- Opraveny některé podmínky, kdy `basic_string` by se obsah řetězců zakódovat. (Poznámka: samoobslužné vkládání do vektorů je standardem stále zakázáno.)
- `basic_string::shrink_to_fit()`již není alokátorem ovlivněn `propagate_on_container_swap`.
- `std::decay`Nyní zpracovává ohavné typy funkcí, to znamená typy funkcí, které jsou cv kvalifikované a/nebo ref-qualified.
- Změněno zahrnují direktivy pro použití správné rozlišování malých a velkých písmen a lomítka, což zlepšuje přenositelnost.
- Opraveno upozornění C4061 "enumerator '*enumerator**enumeration*' v přepnutí výčtu ' není explicitně zpracováno popiskem případu". Toto upozornění je mimo výchozí nastavení a bylo opraveno jako výjimka z obecných zásad standardní knihovny pro upozornění. (Standardní knihovna je **/W4** clean, ale nepokouší se být **/Wall** clean. Mnoho upozornění mimo výchozí nastavení je extrémně hlučných a není určeno k pravidelnému použití.)
- Vylepšené `std::list` kontroly ladění. Seznam iterátorů nyní `operator->()`zkontrolujte a `list::unique()` nyní označí iterátory jako neplatné.
- Opraveno metaprogramování alokátoru `tuple`použití v .

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- `std::partition`nyní volá predikát N krát místo N + 1 krát, jak vyžaduje standard.
- Pokusy vyhnout se magické statiky ve verzi 15.3 byly opraveny ve verzi 15.5.
- `std::atomic<T>`již nevyžaduje `T` být výchozí constructible.
- Haldy algoritmy, které berou logaritmický čas již lineární časový výraz, že vstup je ve skutečnosti haldy při ladění iterátoru je povolena.
- `__declspec(allocator)`je nyní střežen pouze pro C1XX, aby se zabránilo varování od Clang, který nerozumí tomuto declspec.
- `basic_string::npos`je nyní k dispozici jako konstanta času kompilace.
- `std::allocator`V režimu C++ 17 nyní správně zpracovává přidělení přerovnaných typů, `max_align_t`to znamená typy, jejichž zarovnání je větší než , pokud není **zakázáno /Zc:alignedNew-**.  Například vektory objektů s 16bajtovým nebo 32bajtovým zarovnáním jsou nyní správně zarovnány pro pokyny SSE a AVX.

### <a name="conformance-improvements"></a>Vylepšení shody

- Přidali \<\>jsme \<\>všechny `apply()` `make_from_tuple()`, string_view , , .
- \<Přidáno\> \<volitelné\> `shared_ptr::weak_type`, \<varianta ,\>a cstdalign .
- Povolena c++ `constexpr` `min(initializer_list)`14 `minmax(initializer_list)`v `min_element()`, `max_element()` `max(initializer_list)`a `minmax_element()`, a , a .

Další informace naleznete v [tabulce shody jazyků Microsoft C++](../visual-cpp-language-conformance.md).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

- Bylo implementováno několik dalších funkcí jazyka C++17. Další informace naleznete v [tabulce shody jazyků Microsoft C++](cpp-conformance-improvements.md#improvements_153).
- Implementováno P0602R0 "varianta a volitelné by měly šířit kopírování / přesunout triviality".
- Standardní knihovna nyní oficiálně toleruje dynamické RTTI, které jsou zakázány pomocí [/GR-](../build/reference/gr-enable-run-time-type-information.md) možnost. Jak `dynamic_pointer_cast()` `rethrow_if_nested()` a ze `dynamic_cast`své podstaty vyžadují , `=delete` takže standardní knihovna je nyní označí jako pod **/GR-**.
- I když dynamická RTTI byla zakázána přes **/GR-**, `typeid(SomeType)` "statické RTTI" ve formě je stále k dispozici, a pohání několik standardních komponent knihovny. Standardní knihovna nyní podporuje zakázání této funkce příliš, přes **/D\_MÁ\_STATIC\_RTTI = 0**. Tento příznak také `std::any`zakáže , `target()` a `target_type()` členské funkce `std::function`, a `get_deleter()` friend členské funkce `std::shared_ptr` a `std::weak_ptr`.
- Standardní knihovna nyní používá C++ 14 `constexpr` bezpodmínečně, namísto podmíněně definovaných maker.
- Standardní knihovna nyní interně používá aliasové šablony.
- Standardní knihovna `nullptr` nyní používá interně, nikoli `nullptr_t{}`. (Vnitřní použití null byla zásadou. Interní použití 0 jako null se postupně čistí.)
- Standardní knihovna `std::move()` nyní používá interně, místo `std::forward()`stylisticky zneužití .
- `static_assert(false, "message")` Změněno `#error message`na . Tato změna vylepšuje diagnostiku kompilátoru, protože `#error` okamžitě zastaví kompilaci.
- Standardní knihovna již neoznačuje funkce jako `__declspec(dllimport)`. Moderní technologie linkeru to již nevyžaduje.
- Extrahované SFINAE na výchozí argumenty šablony, které snížily nepořádek ve srovnání s návratové typy a typy argumentů funkce.
- Ladicí \<kontroly v\> náhodném nyní používají standardní knihovny `_Rng_abort()` obvyklé `fputs()` stroje, namísto vnitřní funkce, která volala **stderr**. Implementace této funkce je zachována pro binární kompatibilitu, ale byla odebrána v další binární nekompatibilní verzi standardní knihovny.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- Několik standardních funkcí knihovny byly přidány, zastaralé nebo odebrány v souladu se standardem C ++ 17. Další informace naleznete v [tématu C++ vylepšení shody v sadě Visual Studio](cpp-conformance-improvements.md#improvements_155).
- Experimentální podpora následujících paralelních algoritmů:
  - `all_of`
  - `any_of`
  - `for_each`
  - `for_each_n`
  - `none_of`
  - `reduce`
  - `replace`
  - `replace_if`
  - `sort`
- Podpisy pro následující paralelní algoritmy jsou přidány, ale nejsou paralelizovány v tomto okamžiku; profilování nevykazovalo žádný přínos v paralelizaci algoritmů, které pouze přesouvají nebo permutují prvky:
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
- Základy knihovny V1
- Odstranění `polymorphic_allocator` přiřazení
- Zlepšení odpočtu argumentů šablony třídy

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

- Podpora paralelních algoritmů již není experimentální
- Nová implementace \<souborového systému>
- Elementární řetězcové převody (částečné)
- `std::launder()`
- `std::byte`
- `hypot(x,y,z)`
- Zamezení zbytečnému rozkladu
- Matematické speciální funkce
- `constexpr char_traits`
- Vodítka pro odpočty pro standardní knihovnu

Další informace naleznete v [tabulce shody jazyků Microsoft C++](../visual-cpp-language-conformance.md).

### <a name="performance-and-throughput-fixes"></a>Opravy výkonu a propustností

- Přetížení `basic_string::find(char)` volalo `traits::find` jen jednou. Dříve byla implementována jako obecné hledání řetězce pro řetězec délky 1.
- `basic_string::operator==`Nyní zkontroluje velikost řetězce před porovnáním obsahu řetězce.
- Odstraněna řídicí `basic_string`spojka v aplikaci , což bylo pro optimalizátor kompilátoru obtížné analyzovat. Pro všechny krátké řetězce `reserve` volání má stále nenulové náklady nedělat nic.
- `std::vector`byla přepracována z hlediska správnosti a výkonu: aliasování během operací vložení a umístění je nyní správně zpracováno podle požadavků `move_if_noexcept()` standardu, záruka silné výjimky je nyní poskytována, pokud to vyžaduje standard prostřednictvím a jiné logiky, a vložení a umístění provádět méně operací prvku.
- Standardní knihovna jazyka C++ se nyní vyhýbá dereferencování nulových efektních ukazatelů.
- Zlepšený `weak_ptr::lock()` výkon.
- Chcete-li zvýšit propustnost kompilátoru, c++ záhlaví standardní knihovny nyní vyhnout včetně deklarace pro zbytečné kompilátoru vnitřní.
- Vylepšen výkon `std::string` a `std::wstring` přesunout konstruktory více než třikrát.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

- Pracoval kolem interakce, s `noexcept` nimiž `std::atomic` brání vkládání implementace do funkcí, které používají strukturované zpracování výjimek (SEH).
- Změněna interní `_Deallocate()` funkce standardní knihovny pro optimalizaci do menšího kódu, což umožňuje, aby byla vložena do více míst.
- Změněno `std::try_lock()` na použití rozšíření balení namísto rekurze.
- Vylepšenalgoritmus `std::lock()` blokování zablokování `lock()` používat operace namísto předení na `try_lock()` všechny zámky.
- Byla povolena optimalizace `system_category::message()`pojmenovaných vrácené hodnoty v programu .
- `conjunction`a `disjunction` nyní konkretizovat N + 1 typy, namísto 2N + 2 typy.
- `std::function`již nevytváří instance alokátoru podporu stroje pro každý typ-vymazány callable, zlepšení propustnosti a snížení .obj `std::function`velikost v programech, které projdou mnoho různých lambdas na .
- `allocator_traits<std::allocator>`obsahuje ručně vložené `std::allocator` operace, snížení velikosti kódu `std::allocator` v `allocator_traits` kódu, který interaguje pouze prostřednictvím (to znamená ve většině kódu).
- Rozhraní pro alokátor minimální přidělení C ++ 11 `allocator_traits` je nyní zpracována volání standardní knihovny `_Wrap_alloc`přímo, namísto zabalení přidělování do vnitřní třídy . Tato změna snižuje velikost kódu generované pro podporu přidělování, zlepšuje optimalizátor schopnost důvod o standardní knihovny kontejnery v některých případech a poskytuje lepší ladění (jako nyní vidíte typ přidělování, spíše než `_Wrap_alloc<your_allocator_type>` v ladicím programu).
- Odebráno metaprogramování `allocator::reference`pro vlastní , které alokátory nejsou ve skutečnosti povoleno přizpůsobit. (Alokátory mohou způsobit, že kontejnery používají efektní ukazatele, ale ne efektní odkazy.)
- Front-end kompilátoru byl vyučován rozbalit ladicí iterátory v rozsahu založené na smyčkách, zlepšení výkonu ladění sestavení.
- Vnitřní `basic_string` zmenšit `reserve()` cestu a `shrink_to_fit()` již není v cestě přerozdělování operací, snížení velikosti kódu pro všechny mutující členy.
- Vnitřní `basic_string` cesta růstu již není `shrink_to_fit()`v cestě .
- Zmutační `basic_string` operace jsou nyní započítány do nepřidělování rychlé cesty a přidělování funkcí pomalé cesty, takže je pravděpodobnější, že společné no-reallocate případ je vložen do volajících.
- Operace `basic_string` mutování nyní vytvořit přerozděleny vyrovnávací paměti v požadovaném stavu, nikoli změna velikosti na místě. Například vložení na začátku řetězce nyní přesune obsah po vložení přesně jednou (buď dolů nebo do nově přidělené vyrovnávací paměti), namísto dvakrát v případě přerozdělování (do nově přidělené vyrovnávací paměti a potom dolů).
- Operace volající standardní knihovnu\> C `errno` v \<řetězci nyní uvádí adresu do mezipaměti, aby se odstranila opakovaná interakce s tls.
- Zjednodušil `is_pointer` implementaci.
- Byla dokončena změna výrazu SFINAE založeného na funkcích a `struct` `void_t`na základě.
- Standardní algoritmy knihovny se nyní vyhýbají postincrementing iterátory.
- Opravena upozornění na zkrácení při použití 32bitových alokátorů v 64bitových systémech.
- `std::vector`přesunutí přiřazení je nyní efektivnější v případě non-POCMA non-equal-alokátor, opětovné použití vyrovnávací paměti, pokud je to možné.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- `basic_string<char16_t>`nyní zapojuje `memcmp` `memcpy`stejné , a `basic_string<wchar_t>` podobné optimalizace, které se zabývá.
- Omezení optimalizace, které brání vložky funkcí, které jsou vystaveny naší práci "vyhnout se kopírování funkcí" v aktualizaci Visual `lower_bound(iter, iter, function pointer)`Studio 2015 Update 3, bylo zpracováno a obnovení výkonu aplikace .
- Režie `includes`iterátorladění objednávky ověření vstupů do , `set_difference`, `set_symmetric_difference`a `set_union` byla snížena rozbalování iterátory před kontrolou pořadí.
- `std::inplace_merge`nyní přeskočí prvky, které jsou již na místě.
- Konstrukce `std::random_device` již konstrukce a pak zničí `std::string`.
- `std::equal`a `std::partition` měl skip-threading optimalizace projít, který šetří porovnání iterátoru.
- Když `std::reverse` je předán ukazatele triviálně kopírovat , `T`bude nyní odeslána do ručně psané vectorized implementace.
- `std::fill`, `std::equal`a `std::lexicographical_compare` učili se, `memset` `memcmp` jak `std::byte` `gsl::byte` odesílat do a pro a (a další char-jako výčty a výčtu tříd). Vzhledem k tomu, `std::copy` odeslání pomocí `is_trivially_copyable`, to nepotřeboval žádné změny.
- Standardní knihovna již neobsahuje destruktory prázdných závorek, jejichž jediným chováním bylo vytvořit typy netriválně destructible.

## <a name="other-libraries"></a>Další knihovny

### <a name="open-source-library-support"></a>Podpora knihovny s otevřeným zdrojovým kódem

**Vcpkg** je nástroj příkazového řádku s otevřeným zdrojovým kódem, který výrazně zjednodušuje proces získávání a vytváření statických libs a DLLS s otevřeným zdrojovým kódem v sadě Visual Studio. Další informace naleznete [v tématu vcpkg: Správce balíčků pro C++](../build/vcpkg.md).

### <a name="cpprest-sdk-290"></a>CPPRest SDK 2.9.0

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

CPPRestSDK, webové rozhraní API pro různé platformy pro C++, bylo aktualizováno na verzi 2.9.0. Další informace naleznete v tématu [CppRestSDK 2.9.0 je k dispozici na GitHubu](https://devblogs.microsoft.com/cppblog/cpprestsdk-2-9-0-is-available-on-github/).

### <a name="atl"></a>ATL

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- Další sada oprav shody vyhledávání názvů
- Existující konstruktory přesunutí a operátory přiřazení přesunutí jsou nyní správně označeny jako nevrhací
- Uvolnit platné upozornění C4640 o bezpečném přístupu místní chudiny v atlstr.h
- Inicializace místní statiky bezpečná pro přístup z více vláken byla automaticky vypnuta v sadě nástrojů XP při vytváření seznamu ATL, ale nyní není. Můžete přidat **/Zc:threadSafeInit-** v nastavení projektu, pokud je žádoucí inicializace bezpečná pro přístup z více vláken.

### <a name="visual-c-runtime"></a>Visual C++ runtime

- Nové záhlaví "cfguard.h" pro symboly Control Flow Guard.

## <a name="c-ide"></a>C++ IDE

- Výkon při změně konfigurace je teď vyšší u nativních projektů C++ a mnohem vyšší u projektů C++/CLI. Když je konfigurace řešení aktivována poprvé, bude nyní rychlejší a všechny pozdější aktivace této konfigurace řešení budou téměř okamžité.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

- Několik průvodců projektu a kódu je přepsaných ve stylu dialogu podpisu.
- **Přidat třídu** nyní spustí průvodce Přidat třídu přímo. Všechny ostatní položky, které zde byly dříve, jsou nyní k dispozici v části **Přidat > novou položku**.
- Projekty win32 jsou nyní v kategorii **Plocha systému Windows** v dialogovém okně **Nový projekt.**
- Šablony **konzoly systému Windows** a **aplikace pro stolní počítače** nyní vytvářejí projekty bez zobrazení průvodce. Ve stejné kategorii je nový **Průvodce plochami systému Windows,** který zobrazuje stejné možnosti jako starý průvodce **konzolou Win32.**

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

Několik operací jazyka C++, které používají modul IntelliSense pro refaktoring a navigaci kódu, běží mnohem rychleji. Následující čísla jsou založena na řešení Visual Studio Chromium s 3500 projekty:

|||
|-|-|
|Funkce|Zlepšení výkonu|
|přejmenování|5,3x|
|Změnit signaturu |4,5x|
|Najít všechny odkazy|4,7x|

C++ nyní podporuje kombinaci kláves Ctrl+Click **Go To Definition**, takže navigace myší na definice je snadná. Vizualizér struktury z sady Productivity Power Tools je nyní ve výchozím nastavení také součástí produktu.

## <a name="intellisense"></a>IntelliSense

- Ve výchozím nastavení je nyní používán nový databázový stroj využívající SQLite. Tím se urychlí databázové **operace, jako je Přejít na definici** a najít všechny odkazy , a výrazně zlepší počáteční čas **analýzy**řešení. Nastavení bylo přesunuto do **nástroje > možnosti > textový editor > C / C ++ > Advanced** (to bylo dříve pod ... C/C++ | Experimentální).

- Vylepšili jsme výkon technologie IntelliSense u projektů a souborů, které nepoužívají předkompilované hlavičky – pro záhlaví v aktuálním souboru bude vytvořena automatická předkompilovaná hlavička.

- Přidali jsme do seznamu chyb filtrování a nápovědu k chybám technologie IntelliSense. Kliknutí na sloupec s chybami teď umožní je filtrovat. Kromě toho kliknutím na konkrétní chyby nebo stisknutím klávesy F1 spustíte online vyhledávání chybové zprávy.

  ![Seznam chyb](media/ErrorList1.png "Seznam chyb")

  ![Filtrovaný seznam chyb](media/ErrorList2.png "Filtrovaný seznam chyb")

- Přidali jsme možnost filtrovat položky seznamu členů podle typu.

  ![Filtrování seznamu členů](media/mlfiltering.png "Filtrování seznamu členů")

- Byla přidána nová experimentální funkce Predictive IntelliSense, která poskytuje kontextově uvědomující filtrování toho, co se zobrazuje v seznamu členů. Další informace naleznete v tématu [C++ IntelliSense Improvements – Predictive IntelliSense & Filtering](https://devblogs.microsoft.com/cppblog/c-intellisense-improvements-predictive-intellisense-filtering/).
- **Najít všechny reference** (Shift+F12) vám nyní pomůže snadno obejít, a to i ve složitých codebases. Poskytuje pokročilé seskupení, filtrování, řazení, vyhledávání ve výsledcích a (u některých jazyků) vybarvení, takže můžete získat jasnou představu o vašich referencích. Pro C++ nové ui obsahuje informace o tom, zda čteme z nebo zápis do proměnné.
- Funkce změny tečky na šipku technologie IntelliSense se změnila z experimentální na pokročilou a teď je ve výchozím nastavení povolená. Editor funkce **Rozbalit obory** a **Rozbalit prioritu** byly také přesunuty z experimentální na pokročilé.
- Experimentální funkce refaktoringu **Změnit podpis** a **Extrahovat funkce** jsou nyní k dispozici ve výchozím nastavení.
- Byla přidána experimentální funkce "Rychlejší načítání projektu" pro projekty jazyka C++. Při příštím otevření projektu C++ se načte rychleji a čas poté se načte *mnohem* rychleji!
- Některé z těchto funkcí jsou společné pro jiné jazyky a některé jsou specifické pro Jazyk C++. Další informace o těchto nových funkcích naleznete [v tématu Oznámení Visual Studia "15" Preview 5](https://devblogs.microsoft.com/visualstudio/announcing-visual-studio-15-preview-5/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

- Byla přidána podpora pro ClangFormat. Další informace naleznete [v tématu ClangFormat Support in Visual Studio 2017](https://devblogs.microsoft.com/cppblog/clangformat-support-in-visual-studio-2017-15-7-preview-1/).

## <a name="non-msbuild-projects-with-open-folder"></a>Projekty jiné než MSBuild s otevřenou složkou

Visual Studio 2017 zavádí funkci **Otevřít složku,** která umožňuje kódovat, vytvářet a ladit ve složce obsahující zdrojový kód bez nutnosti vytvářet řešení nebo projekty. Teď je mnohem jednodušší začít s Visual Studio, i v případě, že váš projekt není projekt založený na MSBuild. S **otevřenou složkou**získáte přístup k výkonným funkcím principu kódu, úprav, vytváření a ladění, které visual studio již poskytuje pro projekty MSBuild. Další informace naleznete v tématu [Open Folder projects for C++](../build/open-folder-projects-cpp.md).

- Vylepšení prostředí Otevřít složku Můžete přizpůsobit prostředí prostřednictvím těchto souborů JSON:
  - CppProperties.json použijte k přizpůsobení technologie IntelliSense a prostředí procházení.
  - Tasks.json použijte k přizpůsobení kroků sestavení.
  - Launch.json použijte k přizpůsobení prostředí ladění.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

- Vylepšená podpora pro alternativní kompilátory a sestavení prostředí, jako je MinGW a Cygwin. Další informace naleznete [v tématu Použití MinGW a Cygwin s Visual C++ a Otevřít složku](https://devblogs.microsoft.com/cppblog/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/).
- Byla přidána podpora pro definování globálních proměnných prostředí specifických pro konfiguraci v položkách CppProperties.json a CMakeSettings.json. Tyto proměnné prostředí mohou být spotřebovány ladicími konfiguracemi definovanými v souboru launch.vs.json a úkoly v tasks.vs.json. Další informace naleznete [v tématu Přizpůsobení prostředí pomocí vizuálních c++ a otevřené složky](https://devblogs.microsoft.com/cppblog/customizing-your-environment-with-visual-c-and-open-folder/).
- Vylepšená podpora generátoru Ninja společnosti CMake, včetně možnosti snadného cílení na 64bitové platformy.

## <a name="cmake-support-via-open-folder"></a>Podpora CMake prostřednictvím otevřené složky

Visual Studio 2017 zavádí podporu pro použití projektů CMake bez převodu na soubory projektu MSBuild (.vcxproj). Další informace naleznete [v tématu CMake projekty v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md). Otevření projektů CMake s **otevřenou složkou** automaticky konfiguruje prostředí pro úpravy, vytváření a ladění jazyka C++.

- C++ IntelliSense funguje bez nutnosti vytvářet soubor CppProperties.json v kořenové složce. Přidali jsme také novou rozevírací seznam, který uživatelům umožňuje snadno přepínat mezi konfiguracemi poskytovanými soubory CMake a CppProperties.json.

- Prostřednictvím souboru CMakeSettings.json, který je umístěný ve stejné složce jako soubor CMakeLists.txt, se podporuje další konfigurace.

  ![Otevřít složku CMake](media/cmake-cpp.png "Otevřená složka CMake")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

- Přidána podpora pro generátor CMake Ninja.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- Byla přidána podpora pro import existujících mezipamětí CMake.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- Podpora přidána pro CMake 3.11, analýza kódu v projektech CMake, zobrazení Cíle v Průzkumníku řešení, možnosti generování mezipaměti a kompilace jednoho souboru. Další informace naleznete [v tématu CMake Support v sadě Visual Studio](https://devblogs.microsoft.com/cppblog/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) a [Projekty CMake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md).

## <a name="windows-desktop-development-with-c"></a>Vývoj plochy windows s C++

Při instalaci původní úlohy pro C++ teď poskytujeme podrobnější prostředí instalace. Přidali jsme volitelné součásti, které vám umožní vybrat a nainstalovat jen ty nástroje, které potřebujete. Uvedené velikosti instalace pro součásti uvedené v uměle instalaci nejsou přesné a podceňují celkovou velikost.

Když chcete úspěšně vytvářet projekty Win32 v úloze vývoje desktopových aplikací v C++, musíte nainstalovat sadu nástrojů i sadu Windows SDK. Nainstalujte doporučené (vybrané) součásti **VC++ 2017 v141 toolset (x86, x64)** a **Windows 10 SDK (10.0.nnnnn)** a ujistěte se, že to funguje. Pokud nejsou nainstalovány potřebné nástroje, projekty nebudou úspěšně vytvořeny a průvodce přestane reagovat.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

Nástroje pro sestavení Visual C++ (dříve dostupné jako samostatný produkt) jsou teď zahrnuty jako úloha v instalačníslužbě sady Visual Studio. Tato úloha nainstaluje pouze nástroje potřebné k sestavení projektů jazyka C++ bez instalace ide sady Visual Studio. Součástí sady nástrojů v140 i v141 jsou. Sada nástrojů v141 obsahuje nejnovější vylepšení ve Visual Studiu 2017 verze 15.5. Další informace naleznete v [tématu Visual Studio Build Tools now include the VS2017 and VS2015 MSVC Toolsets](https://devblogs.microsoft.com/cppblog/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/).

## <a name="linux-development-with-c"></a>Vývoj linuxových aplikací v jazyce C++

Oblíbené rozšíření [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) je teď součástí sady Visual Studio. Tato instalace nabízí všechno, co potřebujete k vývoji a ladění aplikací v jazyce C++, které se spouštějí v prostředí systému Linux.

##### <a name="visual-studio-2017-version-152"></a>Visual Studio 2017 verze 15.2

Vylepšení byla provedena v cross-platformní sdílení kódu a vizualizace typu. Další informace najdete v [tématu Linux C++ vylepšení pro sdílení kódu napříč platformami a vizualizaci typu](https://devblogs.microsoft.com/cppblog/linux-cross-platform-and-type-visualization/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- Linuxová úloha přidala podporu pro **rsync** jako alternativu k **sftp** pro synchronizaci souborů se vzdálenými počítači Linux.
- Podpora je přidána pro křížové kompilace zaměřené na mikrokontroléry ARM. Chcete-li ji povolit v instalaci, zvolte vývoj Linuxu s úlohami **C++** a vyberte možnost **pro Embedded a IoT Development**. Tato možnost přidá do instalace nástroje pro křížovou kompilaci ARM GCC a provést. Další informace naleznete [v tématu ARM GCC Cross Compilation in Visual Studio](https://devblogs.microsoft.com/cppblog/arm-gcc-cross-compilation-in-visual-studio/).
- Přidána podpora pro CMake. Nyní můžete pracovat na existující základ kódu CMake bez nutnosti převést na projekt sady Visual Studio. Další informace naleznete [v tématu Konfigurace projektu Linux CMake Project](../linux/cmake-linux-project.md).
- Přidána podpora pro spouštění vzdálených úloh. Tato funkce umožňuje spustit libovolný příkaz ve vzdáleném systému, který je definován v programu Visual Studio Connection Manager. Vzdálené úlohy také umožňují kopírování souborů do vzdáleného systému.
Další informace naleznete [v tématu Konfigurace projektu Linux CMake Project](../linux/cmake-linux-project.md).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

- Různá vylepšení scénářů úloh linuxového pracovního vytížení. Další informace naleznete v [tématu Linux C++ zvýšení zatížení projektového systému, Linux Console Window, rsync a připojit k procesu](https://devblogs.microsoft.com/cppblog/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/).
- Technologie IntelliSense pro záhlaví vzdálených připojení k Linuxu. Další informace naleznete [v tématech IntelliSense for Remote Linux Headers](https://devblogs.microsoft.com/cppblog/intellisense-for-remote-linux-headers/) and [Configure a Linux CMake Project](../linux/cmake-linux-project.md).

## <a name="game-development-with-c"></a>Vývoj her v jazyce C++

Využijte naplno potenciál C++ k vytváření profesionálních her využívajících technologii DirectX nebo Cocos2d.

## <a name="mobile-development-with-c-android-and-ios"></a>Vývoj mobilních zařízení s C++ (Android a iOS)

Mobilní aplikace teď můžete vytvářet a ladit pomocí sady Visual Studio, která se umí zaměřit i na Android a iOS.

## <a name="universal-windows-apps"></a>Univerzální aplikace pro Windows

C++ je volitelnou součástí úlohy Universal Windows App.  Upgrade projektů C++ se v tuto chvíli musí provést ručně. Pokud otevřete projekt univerzální platformy Windows cílený na v140 v sadě Visual Studio 2017, musíte vybrat sadu nástrojů platformy v141 na stránkách vlastností projektu, pokud nemáte nainstalovanou Visual Studio 2015.

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>Nové možnosti pro C++ na univerzální platformě Windows (UPW)

Nyní máte nové možnosti pro psaní a balení aplikací jazyka C++ pro univerzální platformu Windows a Windows Store: Infrastrukturu Desktop Bridge můžete použít k balení stávající desktopové aplikace nebo objektu COM pro nasazení prostřednictvím Windows Store nebo prostřednictvím stávajících kanálů pomocí bočního načítání. Nové funkce v systému Windows 10 umožňují přidat funkce UPW do desktopové aplikace různými způsoby. Další informace naleznete [v tématu Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

Je přidána šablona projektu **Projektu balení aplikací systému Windows,** která výrazně zjednodušuje balení desktopových aplikací pomocí aplikace Desktop Bridge. Je k dispozici v části **Soubor | Nové | Projekt | Nainstalováno | Visual C++ | Univerzální platforma Windows**. Další informace najdete [v tématu Balíček aplikace pomocí Visual Studia (Desktop Bridge)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

Při psaní nového kódu můžete nyní použít C++/WinRT, standardní projekci jazyka C++ pro prostředí Windows Runtime implementované výhradně v souborech hlaviček. Umožňuje vytvářet i využívat rozhraní API prostředí Windows Runtime pomocí libovolného kompilátoru jazyka C++ kompatibilního se standardy. C++/WinRT je navržen tak, aby vývojářům jazyka C++ poskytoval prvotřídní přístup k modernímu rozhraní API systému Windows. Další informace naleznete v tématu [C++/WinRT: Moderní jazyk C++ pro prostředí Windows Runtime](https://moderncpp.com/).

Od sestavení 17025 windows SDK Insider Náhled, C ++ /WinRT je součástí sady Windows SDK. Další informace naleznete v tématu [C++/WinRT je nyní součástí sady Windows SDK](https://devblogs.microsoft.com/cppblog/cppwinrt-is-now-included-the-windows-sdk/).

## <a name="clangc2-platform-toolset"></a>Sada nástrojů platformy Clang/C2

Sada nástrojů Clang/C2, která je dodávána s Visual Studio 2017, nyní podporuje přepínač **/bigobj,** který je klíčový pro vytváření velkých projektů. Zahrnuje také několik důležitých oprav chyb, jak ve front-endu, tak v back-endu kompilátoru.

## <a name="c-code-analysis"></a>Analýza kódu jazyka C++

Se sadou Visual Studio se nyní distribuují moduly pro kontrolu jádra C++, které vynucují [pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines). Jednoduše povolte dáma na stránce **Rozšíření analýzy kódu** na stránkách vlastností projektu a rozšíření budou zahrnuta při spuštění analýzy kódu. Další informace naleznete [v tématu Použití kontroly základních pokynů jazyka C++](/cpp/code-quality/using-the-cpp-core-guidelines-checkers).

![CppCoreCheck](media/CppCoreCheck.png "Stránka vlastností CppCoreCheck")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

- Byla přidána podpora pro pravidla související se správou zdrojů.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- Nové kontroly základních pokynů jazyka C++ zahrnují správnost inteligentního ukazatele, správné použití `goto` globálních inicializátorů a označování použití konstrukcí, jako je a chybné přetypování.

- Některá čísla upozornění, která najdete v 15.3, už nejsou k dispozici v 15.5. Tato upozornění byla nahrazena specifičtějšími kontrolami.

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 verze 15.6

- Podpora přidána pro analýzu jednoho souboru a vylepšení výkonu analýzy za běhu. Další informace naleznete v tématu [C++ Static Analysis Improvements for Visual Studio 2017 15.6 Preview 2](https://devblogs.microsoft.com/cppblog/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/)

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

- Podpora přidána pro [/analyze:ruleset](../build/reference/analyze-code-analysis.md), který umožňuje zadat pravidla analýzy kódu ke spuštění.
- Přidána podpora pro další pravidla základních pokynů jazyka C++.  Další informace naleznete [v tématu Použití kontroly základních pokynů jazyka C++](/cpp/code-quality/using-the-cpp-core-guidelines-checkers).

## <a name="unit-testing"></a>Testování jednotek

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

Testovací adaptér Google a boost.test adaptér jsou nyní k dispozici jako **součásti vývoje plochy s úlohou C++** a jsou integrovány s **Průzkumníkem testů**. Podpora CTest je přidána pro projekty Cmake (pomocí otevřené složky), i když úplná integrace s **Průzkumníkem testů** ještě není k dispozici. Další informace naleznete [v tématu Zápis testů částí pro C/C++](/visualstudio/test/writing-unit-tests-for-c-cpp).

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 verze 15.6

- Přidána podpora pro podporu dynamické knihovny Boost.Test.
- Šablona položky Boost.Test je nyní k dispozici v rozhraní IDE.

Další informace naleznete v tématu [Boost.Test Testování částí: Podpora dynamické knihovny a Nová šablona položky](https://devblogs.microsoft.com/cppblog/boost-test-unit-testing-dynamic-library-support-and-new-item-template/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

[Byla přidána](/visualstudio/ide/find-code-changes-and-other-history-with-codelens) podpora CodeLens pro projekty testování částí jazyka C++. Další informace naleznete [v tématu Oznámení CodeLens pro testování částí C++](https://devblogs.microsoft.com/cppblog/announcing-codelens-for-c-unit-testing/).

## <a name="visual-studio-graphics-diagnostics"></a>Diagnostika grafiky sady Visual Studio

Visual Studio Graphics Diagnostics je sada nástrojů pro nahrávání a analýzu problémů s vykreslováním a výkonem v aplikacích Direct3D. Funkce diagnostiky grafiky lze použít s aplikacemi, které jsou spuštěny místně v počítači s Windows, v emulátoru zařízení s Windows nebo na vzdáleném počítači nebo zařízení.

- **Vstupní & výstup pro stínovače vrcholů a geometrií:** Schopnost zobrazit vstup a výstup stínovačů vrcholů a stíničů geometrie byla jednou z nejžádanějších funkcí a nyní je podporována v nástrojích. Jednoduše vyberte fázi VS nebo GS v zobrazení Fáze kanálu a začněte kontrolovat jeho vstup a výstup v následující tabulce.

  ![Vstup/Výstup pro shadery](media/io-shaders.png)

- **Hledat a filtrovat v tabulce objektů:** Poskytuje rychlý a snadný způsob, jak najít zdroje, které hledáte.

  ![Search](media/search.png)

- **Historie zdrojů:** Toto nové zobrazení poskytuje zjednodušený způsob zobrazení celé historie změn prostředku, jak byl použit při vykreslování zachyceného rámce. Chcete-li vyvolat historii pro libovolný prostředek, jednoduše klikněte na ikonu hodiny vedle libovolného hypertextového odkazu prostředku.

  ![Historie zdrojů](media/resource-history.png)

  Zobrazí se nové okno nástroje **Historie zdrojů,** které je naplněno historií změn prostředku.

  ![Změna historie zdrojů](media/resource-history-change.png)

  Pokud byl váš snímek zachycen s povoleným zachycením zásobníku úplného volání **(Visual Studio > Nástroje > možnosti** v části **Diagnostika grafiky),** lze kontext každé události změny rychle odvodit a zkontrolovat v rámci projektu sady Visual Studio.

- **Statistika rozhraní API:** Zobrazení souhrnu využití rozhraní API na vysoké úrovni v rámci. Je to užitečné pro objevování hovorů, které si nemusí uvědomit, že děláte vůbec, nebo hovory, které děláte příliš mnoho. Toto okno je k dispozici prostřednictvím **zobrazení > statistiky rozhraní API** v nástroji Visual Studio Graphics Analyzer.

  ![Statistiky rozhraní API](media/api-stats.png)

- **Statistika paměti:** Zobrazení, kolik paměti ovladač přiděluje pro prostředky, které vytvoříte v rámci. Toto okno je k dispozici prostřednictvím **nástroje View > Memory Statistics** v nástroji Visual Studio Graphics **Analyzer**. Data lze zkopírovat do souboru CSV pro zobrazení v tabulce klepnutím pravým tlačítkem myši a výběrem **příkazu Kopírovat vše**.

  ![Statistiky paměti](media/memory-stats.png)

- **Ověření rámce:** Nový seznam chyb a upozornění poskytuje snadný způsob navigace v seznamu událostí na základě potenciálních problémů zjištěných vrstvou ladění Direct3D. Kliknutím na **Zobrazit > ověření rámce** v nástroji Visual Studio Graphics Analyzer otevřete okno. Potom klepnutím na **tlačítko Spustit ověření** spusťte analýzu. Dokončení může trvat několik minut v závislosti na složitosti rámce.

  ![Ověření rámce](media/frame-validation.png)

- **Analýza snímků pro D3D12:** Pomocí analýzy snímků můžete analyzovat výkon kreslení pomocí řízených experimentů "what-if". Přepněte na kartu Analýza rámce a spusťte analýzu pro zobrazení sestavy. Další podrobnosti najdete ve videu [GoingNative 25: Visual Studio Graphics Frame Analysis.](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool)

  ![Analýza snímků](media/frame-analysis.png)

- **Vylepšení využití GPU:** Otevřené trasování lze převzít pomocí profileru využití gpu sady Visual Studio pomocí nástroje GPU View nebo nástroje WPA (Windows Performance Analyzer) pro podrobnější analýzu. Pokud máte nainstalovanou sadu Nástrojů pro výkon systému Windows, jsou v pravém dolním rohu přehledu relace dva hypertextové odkazy, jeden pro WPA a druhý pro zobrazení GPU.

  ![Využití GPU](media/gpu-usage.png)

  Trasování otevřené v zobrazení GPU prostřednictvím tohoto odkazu podporují synchronizované zvětšování a posouvání na časové ose mezi VS a ZOBRAZENÍ GPU. Zaškrtávací políčko ve VS se používá k řízení, zda je synchronizace povolena nebo ne.

  ![Zobrazení GPU](media/gpu-view.png)

::: moniker-end

::: moniker range="=vs-2015"

Úplný seznam novinek v aktualizaci Visual Studio 2015 Update 3 najdete v [tématu Visual C++ What's New 2003 až 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015). Další informace o novince ve všech Visual Studio 2015 najdete v tématu poznámky k verzi propojené z [Visual Studio 2015 Historie poznámek k verzi](/visualstudio/releasenotes/vs2015-version-history). Informace o tom, co je nového pro C++ ve Visual Studiu 2019, najdete v [tématu Co je nového pro C++ ve Visual Studiu](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019). Informace o tom, co je nového pro C++ ve Visual Studiu 2017, najdete v tématu [Co je nového pro C++ ve Visual Studiu 2017](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017).

::: moniker-end
