---
title: Novinky v jazyce C++ v sadě Visual Studio
ms.date: 06/17/2019
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: b408036fdee3d8163ef48cdbdab6e0f0a9c939ab
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344190"
---
# <a name="whats-new-for-c-in-visual-studio"></a>Novinky v jazyce C++ v sadě Visual Studio

::: moniker range=">=vs-2019"

Visual Studio 2019 přináší řadu vylepšení a oprav prostředí Microsoft C++. Vyřešili jsme mnoho chyb a problémů v kompilátoru a nástrojů. Mnohé z těchto problémů chyby odeslané zákazníky pomocí [nahlásit problém](/visualstudio/how-to-report-a-problem-with-visual-studio-2017) a [poslat návrh](https://developercommunity.visualstudio.com/spaces/62/index.html) možnosti v části **odeslat zpětnou vazbu**. Děkujeme vám, že hlásíte chyby! Další informace o tom, co je nového v celé sady Visual Studio, navštivte web [co je nového ve Visual Studio 2019](/visualstudio/ide/whats-new-visual-studio-2019). Informace o tom, co je nového pro C++ v sadě Visual Studio 2017, najdete v článku [co je nového pro C++ v sadě Visual Studio 2017](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017). Informace o tom, co je nového pro C++ v sadě Visual Studio 2015 a starší verze, najdete v článku [Visual C++ co je nového 2003 do 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="c-compiler"></a>kompilátor C++

- Vylepšená podpora pro funkce C ++ 17 a řeší správnost, a navíc experimentální podporu pro C ++ 20 funkcí jako jsou moduly a korutin. Podrobné informace najdete v tématu [vylepšení shody C++ ve Visual Studio 2019](cpp-conformance-improvements.md).

- `/std:c++latest` Možnost nyní zahrnuje funkce C ++ 20, které nejsou nutně dokončeny, včetně počáteční podporu pro C ++ 20 operátor \<= > ("kosmické lodě") pro třícestné porovnání.

- C++ Přepínač kompilátoru `/Gm` je nyní zastaralá. Zvažte zakázání `/Gm` přepnout ve skriptech sestavení, pokud není výslovně uveden. Ale můžete taky ignorovat upozornění zastarání pro `/Gm`, protože není považováno za chybu při použití "Zpracovávat upozornění jako chyby" (`/WX`).

- MSVC zahájení implementace funkce z C ++ 20 standardní návrhu v rámci `/std:c++latest` příznak `/std:c++latest` je teď kompatibilní s `/clr` (všechny typy), `/ZW`, a `/Gm`. V aplikaci Visual Studio 2019 pomocí `/std:c++17` nebo `/std:c++14` režimy při kompilaci s `/clr`, `/ZW`, nebo `/Gm` (ale najdete v předchozím bodě).

- U aplikací C++ pro konzoly a klasickou pracovní plochu se už negenerují předkompilované hlavičky.

### <a name="codegen-security-diagnostics-and-versioning"></a>CODEGEN, zabezpečení, Diagnostika a správa verzí

Vylepšení analýzy s `/Qspectre` pro poskytování pomoci zmírnění chyby zabezpečení Spectre Variant 1 (CVE-2017-5753). Další informace najdete v tématu [zmírnění hrozby Spectre v MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).

## <a name="c-standard-library-improvements"></a>C++vylepšení standardní knihovny

- Implementace dalších C ++ 17 a C ++ 20 knihovna funkcí a správnost opravy. Podrobné informace najdete v tématu [vylepšení shody C++ ve Visual Studio 2019](cpp-conformance-improvements.md).

- Byl použit clang-Format C++ hlavičky standardní knihovny vylepšenou čitelností.

- Vzhledem k tomu, že Visual Studio teď podporuje pouze můj kód pro C++, standardní knihovna již nemusí poskytnout vlastní mechanismus pro `std::function` a `std::visit` k dosažení stejného výsledku. Odebrání tohoto strojů z velké části nemá žádné viditelné pro uživatele účinky. Jedinou výjimkou je, že kompilátor vytvoří už diagnostiku, která signalizují potíže na řádku 15732480 nebo 16707566 z \<type_traits > nebo \<typ variant >.

## <a name="performancethroughput-improvements-in-the-compiler-and-standard-library"></a>Vylepšení výkonu a propustnost v kompilátoru a standardní knihovny

- Zlepšení propustnosti, včetně tak, jak linker zpracovává vstup a výstup souborů, ale taky popustit doby v souboru PDB typu slučování a vytvoření propojení.

- Přidání základní podpora pro OpenMP SIMD vektorizaci. Můžete povolit pomocí nového přepínače kompilátoru `-openmp:experimental`. Tato možnost umožňuje smyčky opatřen poznámkou `#pragma omp simd` k potenciálně vektorizována. Není zaručeno, vektorizace a smyčky s poznámkami, ale není vektorizována se zobrazí upozornění ohlásil. Žádná klauzule SIMD jsou podporovány. jsou ignorovány a je pokud hlášeno upozornění.

- Přidat nový přepínač příkazového řádku vkládání `-Ob3`, což je mnohem vyššími verzi `-Ob2`. `-O2` (optimalizovat binární soubor pro rychlost) stále zahrnuje `-Ob2` ve výchozím nastavení. Pokud zjistíte, že kompilátor nebude vložené dostatečně agresivně, zvažte možnost předávání `-O2 -Ob3`.

- Pro podporu ručně vektorizaci smyčky s voláními matematických knihovních funkcí a určité operace jako dělení celého čísla, přidali jsme podporu pro vnitřní funkce krátkého vektoru matematické knihovny (SVML). Tyto funkce compute ekvivalenty vektoru 128-bit, bitů na 256 nebo 512 bitů. Definice podporovaných funkcí najdete v příručce [Intel Intrinsic Guide](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML).

- Nové a vylepšené optimalizace:

  - Konstanta skládání a aritmetické zjednodušení pro výrazy pomocí vnitřní funkce vektoru SIMD, pro plovoucí desetinnou čárkou a celočíselné formuláře.

  - Výkonnější analýzy pro extrahování informací z toku řízení (příkazy if/else/přepínače) Chcete-li odebrat větve vždy prověřené být true nebo false.

  - Vylepšené memset rozvinutí použít SSE2 vektoru.

  - Vylepšené odebrání kopií zbytečné struktury nebo třídy, zejména pro programy v jazyce C++, které předávají podle hodnoty.

  - Vylepšená optimalizace kódu pomocí `memmove`, jako například `std::copy` nebo `std::vector` a `std::string` konstrukce.

- Optimalizované fyzické návrhu standardní knihovny, aby kompilace součástí standardní knihovny zahrnuté přímo. Tato změna vyjmout dobu sestavení prázdný soubor, který obsahuje pouze \<vektoru > na polovinu. V důsledku toho je nutné přidat `#include` direktivy pro hlavičky, které byly dříve nepřímo zahrnuté. Například kód, který používá `std::out_of_range` teď může být nutné přidat `#include <stdexcept>`. Kód, který používá operátor vkládání datového proudu může teď musíte přidat `#include <ostream>`. Výhodou je, že pouze překlad jednotky jejího použití \<stdexcept – > nebo \<ostream > součásti platit propustnost náklady na jejich kompilace.

- `if constexpr` bylo použito na více místech ve standardní knihovně pro vylepšenou propustnost a snížená kód velikost do operací kopírování, permutací jako reverzní a otočit a knihovna paralelních algoritmů.

- Standardní knihovna teď interně používá `if constexpr` snížit dobu potřebnou ke kompilaci, dokonce i v režim C ++ 14.

- Dynamické propojení zjišťování už paralelní algoritmy knihovny runtime používá k ukládání pole ukazatel funkce celou stránku. Označení tuto paměť jen pro čtení byla považována za již nejsou relevantní pro účely zabezpečení.

- `std::thread`pro konstruktor už čeká na spuštění vlákna a už vloží tolik vrstvy funkce volání mezi základní knihovny jazyka C `_beginthreadex` a zadaný volatelný objekt. Dříve `std::thread` 6 funkce mezi `_beginthreadex` a zadaný volatelný objekt, který bylo sníženo na pouze 3 (2, které jsou právě `std::invoke`). Tato změna také řeší chyby skrytého časování, kde `std::thread` konstruktor způsoboval, že pokud jsou systémové hodiny změnili přesně v okamžiku `std::thread` byla právě vytvořena.

- Oprava regrese výkonu v `std::hash` , který jsme představili při implementaci `std::hash<std::filesystem::path>`.

- Standardní knihovna teď používá destruktory místo bloky catch na několika místech zajistit správnost. Tato změna má za následek lepší interakci ladicího programu: Výjimky můžete vyvolat prostřednictvím standardní knihovny v ovlivněných umístění nyní zobrazují jako vyvolávána z jejich původní výjimku lokality, nikoli naše přegenerování. Byly odstraněny všechny bloky catch standardní knihovny; Očekáváme, že počet bloků catch snížení v pozdějších verzích MSVC.

- Neoptimální codegen v `std::bitset` způsobila pomocí podmíněného throw uvnitř noexcept funkce opravena ve které budou zohledňovat si aktivační cesta.

- `std::list` a `std::unordered_*` – ladění iterátorů řady interně použít na více místech.

- Několik `std::list` členy byly změněny opakovaně používat seznam uzlů, kde je to možné, namísto rušení přidělení a změna jejich přidělení. Mějme například `list<int>` , že už má velikost 3, volání `assign(4, 1729)` nyní přepíše celá čísla v první 3 seznamu uzlů a přiděluje jeden nový uzel s hodnotou 1729 seznamu.

- Všechna volání standardní knihovny `erase(begin(), end())` byly změněny na `clear()`.

- `std::vector` Nyní se inicializuje a vymaže prvky v některých případech efektivněji.

- Vylepšení `std::variant` provádět více optimalizace zařízení, což vede k lepší generovaného kódu. Vkládání kódu je teď mnohem lepší s `std::visit`.

## <a name="c-ide"></a>C++ IDE

### <a name="live-share-c-support"></a>Živá podpora C++ sdílené složky

[Live sdílené složky](/visualstudio/liveshare/) teď podporuje C++, což vývojářům, kteří používají Visual Studio nebo Visual Studio Code pro spolupráci v reálném čase. Další informace najdete v tématu [oznámení Live Share jazyka C++: V reálném čase sdílení a spolupráce](https://devblogs.microsoft.com/cppblog/cppliveshare/)

### <a name="intellicode-for-c"></a>IntelliCode jazyka C++

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 version 16.1

IntelliCode je volitelné rozšíření, které pokud chcete změnit to, co nejpravděpodobněji použijete v horní části seznamu pro doplňování používá vlastní rozsáhlé školení a kontext kódu. Často se může eliminovat potřebu procházejte seznam. Pro C++, IntelliCode nabízí nejvíce pomoc při používání oblíbených knihoven například standardní knihovny. Je k dispozici jako součást úlohy v instalačním programu. Další informace najdete v tématu [AI-Assisted kódu dokončení návrhy přijdou do C++ prostřednictvím IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/).

### <a name="template-intellisense"></a>Šablona IntelliSense

**Šablony panel** teď používá **náhled okno** uživatelského rozhraní, nikoli modální okno podporuje vnořené šablony a předem naplní žádné výchozí argumenty do **náhled okno**. Další informace najdete v tématu [šablony vylepšení technologie IntelliSense pro Visual Studio. 2019 ve verzi Preview 2](https://devblogs.microsoft.com/cppblog/template-intellisense-improvements-for-visual-studio-2019-preview-2/). A **naposledy použitých** rozevírací seznam v **šablony panel** umožňuje rychle přepínat mezi předchozí sadu argumentů vzorku.

### <a name="new-start-window-experience"></a>Nové počáteční zkušenosti okna

Při spuštění rozhraní IDE, zobrazí se nové okno spuštění s možnostmi otevřít posledních projektů, klonování kódu ze správy zdrojového kódu, otevřete místní kód jako řešení nebo složku nebo vytvořte nový projekt. Dialogové okno Nový projekt také přepracovali jsme do prostředí pro vyhledávání a filtrování.

### <a name="new-names-for-some-project-templates"></a>Nové názvy pro některé šablony projektu

Upravili jsme několik názvy šablon projektů a popisy podle s aktualizovanou dialogu Nový projekt.

### <a name="various-productivity-improvements"></a>Různá vylepšení produktivity

Visual Studio 2019 zahrnuje následující funkce, které vám pomohou zajistit psaní kódu, jednodušší a intuitivnější:

- Rychlé opravy pro:
  - Přidat chybějící #include
  - NULL, pokud chcete nullptr
  - Přidat chybějící středníkem
  - Vyřešit chybí obor názvů nebo oboru
  - Nahraďte operandy chybný dereference (\* k & a & \*)
- Rychlé informace pro blok ukázáním na pravé složené závorky
- Operace Peek záhlaví / soubor kódu
- Přejít k definici #include otevře soubor

Další informace najdete v tématu [vylepšení produktivity C++ v sadě Visual Studio. 2019 ve verzi Preview 2](https://devblogs.microsoft.com/cppblog/c-productivity-improvements-in-visual-studio-2019-preview-2/).

### <a name="quickinfo-improvements"></a>Vylepšení rychlé informace

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 version 16.1

Popisek rychlé informace nyní respektuje sémantické zbarvení editoru. Je také nové **vyhledávání Online** odkaz, který bude hledat online dokumentace pro další informace o kterou se najelo myší kód konstrukce. Červená nakreslili kódu bude odkazu uvedeného rychlé informace vyhledejte chybu online. Tímto způsobem není nutné znovu zadat zprávu do prohlížeče. Další informace najdete v tématu [rychlé informace o vylepšení v aplikaci Visual Studio 2019: Barevné zvýrazňování a Online hledání](https://devblogs.microsoft.com/cppblog/quick-info-improvements-in-visual-studio-2019-colorization-and-search-online/).

### <a name="intellicode-available-in-c-workload"></a>K dispozici v IntelliCode C++ pracovního vytížení

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 version 16.1

IntelliCode je nyní dodávána jako volitelná součást v **Desktop Development with C++**  pracovního vytížení. Další informace najdete v tématu [vylepšené C++ IntelliCode se nyní dodává s Visual Studio 2019](https://devblogs.microsoft.com/cppblog/improved-c-intellicode-now-ships-with-visual-studio-2019/).

## <a name="cmake-support"></a>Podpora CMake

- Podpora CMake 3.14

- Visual Studio teď můžete otevřít stávající mezipaměti CMake generovaných externí nástroje, jako je například CMakeGUI, systémy meta sestavení nebo skripty sestavení, které vyvolají cmake.exe sami.

- Vylepšený výkon technologie IntelliSense.

- Nový editor nastavení poskytuje alternativu k ruční úpravě souboru CMakeSettings.json a poskytuje některé parity CMakeGUI.

- Visual Studio vám pomůže rozběhnout vývoj v jazyce C++ s nástroji CMake na Linuxu díky rozpoznání, jestli máte na počítači s Linuxem kompatibilní verzi CMake. Pokud ne, aplikace vám nabídne její instalaci.

- V editoru JSON a chyby v seznamu chyb zobrazovat nekompatibilní nastavení v cmakesettings na pozici, například neodpovídající architektury nebo nekompatibilní nastavení generátoru CMake, podtržení vlnovkou.

- Po spuštění příkazu `vcpkg integrate install` se automaticky rozpozná sada nástrojů vcpkg a povolí se pro projekty CMake, které jsou otevřené v integrovaném vývojovém prostředí. Toto chování můžete vypnout tak, že v nástroji CMakeSettings zadáte prázdný soubor sady nástrojů.

- Projekty CMake teď ve výchozím nastavení aktivují ladění s možností Pouze můj kód.

- Upozornění statické analýzy u projektů CMake teď můžete zpracovat na pozadí a zobrazit v editoru.

- Podřazenými vytvořit a konfigurovat zprávy "begin" a "end" pro projekty CMake a podporu pro průběh sestavení sady Visual Studio uživatelského rozhraní. Kromě toho je teď k dispozici CMake podrobností nastavení **nástroje > Možnosti** přizpůsobení úroveň podrobností CMake sestavení a konfiguraci zprávy v okně výstup.

- `cmakeToolchain` Nastavení je nyní podporována v souboru CMakeSettings.json k určení sady nástrojů bez ruční úpravy CMake příkazového řádku.

- Nový **sestavení všechny** zástupce v nabídce **Ctrl + Shift + B**.

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 version 16.1

- Integrovaná podpora pro úpravy, sestavování a ladění projektů CMake, s Clang/LLVM. Další informace najdete v tématu [Clang/LLVM podpory v sadě Visual Studio](https://devblogs.microsoft.com/cppblog/clang-llvm-support-in-visual-studio/).

## <a name="linux-and-the-windows-subsystem-for-linux"></a>Systémy Linux a subsystém Windows pro Linux

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 version 16.1

- Podpora pro [AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) v projektech pro různé platformy operačních systémů Linux a CMake. Další informace najdete v tématu [AddressSanitizer (ASan) pro Linux úlohy v aplikaci Visual Studio 2019](https://devblogs.microsoft.com/cppblog/addresssanitizer-asan-for-the-linux-workload-in-visual-studio-2019/).

- Integrovaná podpora sady Visual Studio pomocí C++ s subsystém Windows pro Linux (WSL). Další informace najdete v tématu [ C++ s Visual Studio 2019 a subsystém Windows pro Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/).

## <a name="incredibuild-integration"></a>IncrediBuild integrace

IncrediBuild je jako volitelná součást v **vývoj desktopových aplikací pomocí C++**  pracovního vytížení. Sestavení monitorování IncrediBuild je plně integrovaná v integrovaném vývojovém prostředí sady Visual Studio. Další informace najdete v tématu [vizualizovat vaše sestavení se vytváření monitorování a Visual Studio 2019 Nerušivá](https://devblogs.microsoft.com/cppblog/visualize-your-build-with-incredibuilds-build-monitor-and-visual-studio-2019/).

## <a name="debugging"></a>Ladění

- Pro aplikace C++ běžící na Windows soubory PDB nyní načíst v samostatném procesu 64-bit. Tato změna řeší celou řadu chyb způsobených ladicí program spuštěn nedostatek paměti při ladění aplikace, které obsahují velký počet modulů a soubory PDB.

- Vyhledávání se povolí, v **Watch**, **automatické hodnoty**, a **lokální** systému windows.

## <a name="windows-desktop-development-with-c"></a>Vývoj pro plochu Windows v C++

- Už nejsou k dispozici průvodců C++ knihovny ATL/MFC:

  - Průvodce komponentami ATL COM+ 1.0
  - Průvodce komponentami ATL Active Server Pages
  - Průvodce zprostředkovatelem ATL OLE DB
  - Průvodce stránkou vlastností ATL
  - Průvodce příjemcem ATL OLE DB
  - Příjemce ODBC knihovny MFC
  - Třída knihovny MFC z ovládacího prvku ActiveX
  - Třída knihovny MFC z typu Lib.

  Ukázkový kód pro tyto technologie v Microsoft Docs a úložišti VCSamples GitHub archivuje.

- V instalačním programu sady Visual Studio už není dostupná sada Windows 8.1 SDK. Doporučujeme, abyste že vaše projekty C++ upgradujete na nejnovější sadu Windows 10 SDK. Pokud máte pevné závislost na 8.1, můžete ji stáhnout z archivní úrovně sady Windows SDK.

- V nejnovější sadě nástrojů C++ už nebude k dispozici cílení na Windows XP. XP cílení knihovny a kompilátorem MSVC úrovni sady VS 2017 se nadále podporují a lze ji nainstalovat prostřednictvím "Jednotlivé komponenty."

- Naše dokumentace aktivně odrazuje od používání slučovacích modulů k nasazení modulu Runtime Visual C++. Přesměrujeme na další krok této verzi označení naše MSMs jako zastaralé. Zvažte migraci centrálního nasazení VCRuntime z balíčků MSM na balíček opětovné distribuce.

## <a name="mobile-development-with-c-android-and-ios"></a>Vývoj mobilních aplikací pomocí C++ (Android a iOS)

Výchozím prostředím C++ Android je nyní Android SDK 25 a Android NDK 16b.

## <a name="clangc2-platform-toolset"></a>Sada nástrojů platformy clang/C2

Odebrali jsme součástí experimentální Clang/C2. Použijte sadu nástrojů MSVC pro úplné dodržování standardů C++ s `/permissive-` a `/std:c++17`, nebo sada nástrojů Clang/LLVM pro Windows.

## <a name="code-analysis"></a>Analýza kódu

- Analýza kódu se teď spouští automaticky na pozadí. Upozornění se v editoru během psaní podtrhávají zelenou vlnovkou. Další informace najdete v tématu [analýzy kódu v editoru v sadě Visual Studio. 2019 ve verzi Preview 2](https://devblogs.microsoft.com/cppblog/in-editor-code-analysis-in-visual-studio-2019-preview-2/).

- Nová experimentální atribut ConcurrencyCheck pravidla pro dobře známé standardní typy knihoven ze \<vzájemně vyloučený přístup > záhlaví. Další informace najdete v tématu [souběžného zpracování analýzy kódu v aplikaci Visual Studio 2019](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/).

- Aktualizované částečnou implementaci [požadovaných součástí profilu životnost](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/), který zjistí nepropojená ukazatele a reference. Další informace najdete v tématu [životního cyklu aktualizace profilu v sadě Visual Studio. 2019 ve verzi Preview 2](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/).

- Další související korutina kontrol, včetně C26138, C26810, C26811 a experimentální pravidlo C26800. Další informace najdete v tématu [nový kód analýzy kontroluje v aplikaci Visual Studio 2019: použití po přesunutí a pomocné rutiny](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/).

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019 version 16.1

- Nové rychlé opravy pro neinicializované proměnné kontroly. Další informace najdete v tématu [nový kód analýzy rychlých oprav pro neinicializované paměti (C6001) a použití, než init (C26494) upozornění](https://devblogs.microsoft.com/cppblog/new-code-analysis-quick-fixes-for-uninitialized-memory-c6001-and-use-before-init-c26494-warnings/).

## <a name="unit-testing"></a>Testování jednotek

Šablona spravovaného testovacího projektu C++ už není dostupná. Můžete pokračovat v používání rozhraní pro testování spravovaných C++ ve svých existujících projektech. Pro nové jednotkové testy, zvažte použití jedné nativní testovacích platforem, pro které sada Visual Studio obsahuje šablony (MSTest, Google Test) nebo spravované C# šablona projektu pro Test.

::: moniker-end

::: moniker range="=vs-2017"

Visual Studio 2017 přináší řadu vylepšení a oprav prostředí C++. Jsme opravili víc než 250 chyb a nahlášených problémů v kompilátoru a nástrojů, řadu z nich odeslali zákazníci přes [nahlásit problém a poslat návrh](/visualstudio/how-to-report-a-problem-with-visual-studio-2017) možnosti v části **odeslat zpětnou vazbu**. Děkujeme vám, že hlásíte chyby! Další informace o tom, co je nového v celé sady Visual Studio, naleznete v tématu [co je nového v sadě Visual Studio 2017](/visualstudio/ide/whats-new-visual-studio-2017?view=vs-2017). Informace o tom, co je nového pro C++ v aplikaci Visual Studio 2019, naleznete v tématu [co je nového pro C++ v sadě Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019). Informace o tom, co je nového pro C++ v sadě Visual Studio 2015 a starší verze, najdete v článku [Visual C++ co je nového 2003 do 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="c-compiler"></a>kompilátor C++

### <a name="c-conformance-improvements"></a>Vylepšení shody C++

V této verzi jsme kompilátor jazyka C++ a standardní knihovny doplnili rozšířenou podporou pro funkce C++11 a C++14, a také předběžnou podporou pro některé funkce očekávané ve standardu C++17. Podrobné informace najdete v tématu [vylepšení shody C++ v sadě Visual Studio 2017](cpp-conformance-improvements.md).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

Kompilátor podporuje přibližně 75 % funkcí, které jsou nové v C ++ 17, včetně strukturovaných vazeb `constexpr` výrazy lambda, `if constexpr`, vložených proměnných, přeložte výrazy a přidání `noexcept` do systému typů. Tyto funkce jsou dostupné v rámci **/std: c ++ 17** možnost. Další informace najdete v tématu [vylepšení shody C++ v sadě Visual Studio 2017](cpp-conformance-improvements.md)

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

Sada nástrojů kompilátoru MSVC v sadě Visual Studio verze 15.7 nyní odpovídá standardu jazyka C++. Další informace najdete v tématu [Announcing: MSVC splňuje C++ Standard](https://devblogs.microsoft.com/cppblog/announcing-msvc-conforms-to-the-c-standard/) a [shoda jazyka C++ společnosti Microsoft](../visual-cpp-language-conformance.md).

### <a name="new-compiler-options"></a>Nové možnosti kompilátoru

- [/permissive-](../build/reference/permissive-standards-conformance.md): Povolit všechny možnosti kompilátoru shoda přísné standardy a zakázat většina kompilátoru rozšíření specifické pro společnost Microsoft (ale ne `__declspec(dllimport)`, například). Tato možnost zapnutá ve výchozím nastavení v sadě Visual Studio 2017 verze 15.5.  **/ Permissive-** režim přizpůsobení zahrnuje podporu pro dvoufázové vyhledávání názvů. Další informace najdete v tématu [vylepšení shody C++ v sadě Visual Studio](cpp-conformance-improvements.md).

- [/ Diagnostics](../build/reference/diagnostics-compiler-diagnostic-options.md): Povolte zobrazení číslo řádku, číslo řádku a sloupce, nebo číslo řádku a sloupce a blikající kurzor pod řádkem kódu, kde byla nalezena diagnostických chyb nebo upozornění.

- [/ Debug: fastlink](../build/reference/debug-generate-debug-info.md): Povolit až 30 % rychlejší přírůstkové propojení vyprší (vs. Visual Studio 2015) není zkopírováním všechny informace o ladění do souboru PDB. Soubor PDB se místo toho odkazuje na informace o ladění pro soubory objektů a knihovny použité k vytvoření spustitelného souboru. Zobrazit [cyklus v sadě Visual Studio "15" s/Debug: fastlink sestavení C++ rychleji](https://devblogs.microsoft.com/cppblog/faster-c-build-cycle-in-vs-15-with-debugfastlink/) a [doporučení k urychlení sestavení C++ v sadě Visual Studio](https://devblogs.microsoft.com/cppblog/recommendations-to-speed-c-builds-in-visual-studio/).

- Visual Studio 2017 umožňuje používat [/SDL](../build/reference/sdl-enable-additional-security-checks.md) s [/ await](../build/reference/await-enable-coroutine-support.md). Odebrali jsme [/RTC](../build/reference/rtc-run-time-error-checks.md) omezení u Korutin.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- [/ std: c ++ 14 a/std: c ++ nejnovější](../build/reference/std-specify-language-standard-version.md): Tyto možnosti kompilátoru umožňují vyjádřit výslovný souhlas pro konkrétní verze ISO C++ programovací jazyk v projektu. Většina konceptu nové funkce na úrovni standard jsou strážený **/std: c ++ nejnovější** možnost.

- [/ std: c ++ 17](../build/reference/std-specify-language-standard-version.md) umožňuje sadu funkcí C ++ 17 implementované kompilátorem. Tato možnost zakáže kompilátoru a standardní knihovny podpora pro funkce, které se mění nebo nového ve verzích konceptu práce a defect aktualizace standardu jazyka C++ za C ++ 17. Chcete-li povolit tyto funkce, použijte **/std: c ++ nejnovější**.

### <a name="codegen-security-diagnostics-and-versioning"></a>CODEGEN, zabezpečení, Diagnostika a správa verzí

Tato verze přináší několik vylepšení optimalizace, generování kódu, nástrojů pro správu verzí a Diagnostika. Mezi důležitá vylepšení patří:

- Generování vylepšené kódu smyček: Podpora automatické vektorizace dělení konstantních celých čísel, lepší identifikace vzorů memset.
- Vylepšené kód zabezpečení: Vylepšená emise diagnostiky kompilátoru přetečení vyrovnávací paměti, a [/Guard: CF](../build/reference/guard-enable-control-flow-guard.md) teď chrání příkazy switch, které generují tabulku skoků.
- Správa verzí: Hodnota předdefinované makro preprocesoru  **\_MSC\_VER** je nyní monotónně aktualizují při každé aktualizaci nástrojů Visual C++. Další informace najdete v tématu [verze kompilátoru Visual C++](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/).
- Nové rozložení sady nástrojů: Kompilátor a nástroje pro související sestavení mají novou strukturu umístění a adresáře na vývojovém počítači. Nové rozložení umožňuje-souběžnými instalacemi více verzí kompilátoru. Další informace najdete v tématu [kompilátoru rozložení nástroje v sadě Visual Studio 2017](https://devblogs.microsoft.com/cppblog/compiler-tools-layout-in-visual-studio-15/).
- Vylepšená Diagnostika: V okně výstupu teď zobrazuje sloupec, kde dojde k chybě. Další informace najdete v tématu [vylepšení diagnostiky kompilátoru C++ v sadě Visual Studio "15" Preview 5](https://devblogs.microsoft.com/cppblog/c-compiler-diagnostics-improvements-in-vs-15-rc/).
- Při používání společných rutin, experimentální klíčové slovo **yield** (k dispozici v rámci **/ await** možnost) byla odebrána. Váš kód by měl být aktualizován na použití `co_yield` místo. Další informace najdete v tématu [ `yield` – klíčové slovo se `co_yield` v sadě VS 2017](https://devblogs.microsoft.com/cppblog/yield-keyword-to-become-co_yield-in-vs-2017/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

Další vylepšení diagnostiky v kompilátoru. Další informace najdete v tématu [vylepšení diagnostiky v sadě Visual Studio 2017 15.3.0](https://devblogs.microsoft.com/cppblog/diagnostic-improvements-in-vs2017-15-3-0/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

Výkon sady Visual C++ runtime neustále zlepšuje kvůli lepší kvalitu generovaného kódu. Nyní můžete jenom znovu zkompilovat kód a vaše aplikace běží rychleji. Některé optimalizace kompilátoru jsou úplně nové, jako je například vektorizaci podmíněných skalárních úložišť, kombinování volání `sin(x)` a `cos(x)` do nového `sincos(x)`a odstranění redundantní pokyny od Optimalizátor SSA. Další optimalizace kompilátoru jsou vylepšení stávajících funkcí, jako je například heuristiku vektorizéru pro podmíněné výrazy, lepší optimalizace smyčky a plovoucí codegen min/max. Propojovací program má nový a rychlejší **/OPT:ICF** implementaci, což může znamenat až 9 % odkaz – urychlení a existují další opravy výkonu v přírůstkové propojení. Další informace najdete v tématu [/OPT (optimalizace)](../build/reference/opt-optimizations.md) a [Parametr/incremental (Inkrementální odkaz)](../build/reference/incremental-link-incrementally.md).

Microsoft C++ kompilátor podporuje společnosti Intel AVX-512, včetně instrukcí pro délku vektoru, které přinášejí nové funkce v AVX-512 do 128 bitů a 256bitových širokých registrů.

[/Zc:noexceptTypes-](../build/reference/zc-noexcepttypes.md) možnosti je možné vrátit zpět do C ++ 14 verze `noexcept` přitom C ++ 17 režim obecně. Tato možnost vám umožní aktualizovat váš zdrojový kód tak, aby odpovídal C ++ 17, aniž byste museli přepsat všechny vaše `throw()` kódu ve stejnou dobu. Další informace najdete v tématu [odebrání specifikace dynamických výjimek a noexcept](cpp-conformance-improvements.md#noexcept_removal).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

- Nový přepínač kompilátoru [/qspectre](../build/reference/qspectre.md) zmírnit před útoky na straně kanálu spekulativního spouštění. Další informace najdete v tématu [zmírnění hrozby Spectre v MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).
- Nové diagnostické upozornění pro zmírnění hrozby Spectre. Další informace najdete v tématu [chyby zabezpečení Spectre diagnostiky v sadě Visual Studio 2017 verze 15.7 Preview 4](https://devblogs.microsoft.com/cppblog/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/).
- Nová hodnota pro /Zc, **přepínače/Zc:** , umožňuje opravit, vytváření sestav C++ standardní podporu. Například pokud přepínač nastavený a kompilátor probíhá/std: c ++ 17 režimu rozšíří hodnotu **201703 L**. Další informace najdete v tématu [MSVC nyní správně hlásí __cplusplus](https://devblogs.microsoft.com/cppblog/msvc-now-correctly-reports-__cplusplus/).

## <a name="c-standard-library"></a>C++standardní knihovny

### <a name="correctness-improvements"></a>Vylepšení správnosti

##### <a name="visual-studio-2017-rtm-version-150"></a>Visual Studio 2017 RTM (verze 15.0)

- Vedlejší `basic_string` `_ITERATOR_DEBUG_LEVEL != 0` vylepšení diagnostiky. Přeskočení kontroly IDL v sadě řetězců teď oznámí konkrétní chování, které toto přeskočení způsobilo. Například místo zprávy oznamující, že iterátor řetězce nejde přesměrovat, se teď zobrazí zpráva s oznámením, že iterátor řetězce nejde přesměrovat, protože je mimo rozsah (např. je to koncový iterátor).
- Oprava `std::promise` operátor přiřazení přesunu, který dříve mohl způsobit zablokování kódu napořád.
- Oprava chyb kompilátoru s `atomic<T*>` implicitní převod na `T*`.
- `pointer_traits<Ptr>` nyní správně rozpozná `Ptr::rebind<U>`.
- Oprava chybějící `const` kvalifikátoru v `move_iterator` operátor odčítání.
- Oprava bezobslužné nesprávné funkce codegen pro stavové uživatelem definované alokátory vyžadující `propagate_on_container_copy_assignment` a `propagate_on_container_move_assignment`.
- `atomic<T>` Nyní toleruje přetížený `operator&()`.
- Mírně Vylepšená Diagnostika kompilátoru pro nesprávná `bind()` volání.

Úplný seznam vylepšení standardní knihovny v sadě Visual Studio 2017 RTM, najdete v článku C++ blogu týmu [standardní knihovny řeší ve VS 2017 RTM](https://devblogs.microsoft.com/cppblog/stl-fixes-in-vs-2017-rtm/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Kontejnery standardní knihovny nyní Uchytit jejich `max_size()` k `numeric_limits<difference_type>::max()` místo `max()` z `size_type`. Tato změna zajišťuje, že výsledek `distance()` na iterátorech z tohoto kontejneru je reprezentovatelné v návratovém typu `distance()`.
- Oprava chybějící specializace `auto_ptr<void>`.
- `for_each_n()`, `generate_n()`, A `search_n()` algoritmy dříve kompilace se nezdařila. Pokud délka argument nebyl uveden celočíselného typu; nyní pokusu o převod – neintegrální délky iterátory `difference_type`.
- `normal_distribution<float>` už vydá upozornění ve standardní knihovně o zúžení double uvolnění.
- Oprava některých `basic_string` operace, které používají `npos` místo `max_size()` při kontrole přetečení maximální velikosti.
- `condition_variable::wait_for(lock, relative_time, predicate)` by počkejte po celou dobu relativní v případě nesprávné probuzení. Nyní bude čekat pouze jeden interval relativní časové.
- `future::get()` Nyní zruší platnost `future`, jak vyžaduje standard.
- `iterator_traits<void *>` umožňuje být závažná chyba, protože se pokusil formuláře `void&`; nyní čistě stane prázdnou strukturu k povolení použití `iterator_traits` v "je iterátor" sfinae u podmínek.
- Upozornění hlášených Clang **wsystem –--headers** jsme vyřešili.
- Také vyřešili "specifikace výjimky v deklaraci neodpovídá předchozí deklaraci" hlášených Clang **- Wmicrosoft-výjimky spec**.
- Seznam inicializátorů paměť pořadí upozornění hlášených Clang a C1XX také vyřešili.
- Neseřazené kontejnery neměli Prohodit jejich funkce hash nebo predikáty když byli vyměněni kontejnery sami. Nyní dělají.
- Operace prohození mnoho kontejnerů jsou nyní označeny `noexcept` (jak naši standardní knihovnu nikdy si klade za cíl vyvolání výjimky, při zjištění non -`propagate_on_container_swap` bez rovná allocator nedefinované chování podmínky).
- Mnoho `vector<bool>` operace jsou nyní označeny `noexcept`.
- Standardní knihovna teď bude vynucovat odpovídající allocator `value_type` (v C ++ 17 režimu) s výslovného nesouhlasu s únikový poklop.
- Oprava některé podmínky, kde samoobslužné-range-insert into `basic_string` by promíchání obsahu řetězce. (Poznámka: standardní stále zakazuje automatické-range-insert into vektory.)
- `basic_string::shrink_to_fit()` je již nejsou ovlivněny přidělujícího modulu `propagate_on_container_swap`.
- `std::decay` Nyní typy abominable funkce obslužné rutiny, tedy funkce typy, které jsou kvalifikované cv a/nebo kvalifikaci ref.
- Změnit direktiv použití správné rozlišování velikosti písmen a lomítka, zlepšit přenositelnost.
- Oprava upozornění C4061 "výčet"*enumerátor*"v přepnutí výčtu'*výčet*" není explicitně zpracován popisek případu ". Toto upozornění je mimo výchozí a byla stanovena jako výjimku do standardní knihovny obecné zásady pro upozornění. (Standardní knihovna je **/W4** vyčištění, ale nebude se pokoušet být **/Wall** vyčistit. Mnoho vypnout výchozím upozornění jsou extrémně hlučného a nejsou určeny k použití v pravidelných intervalech.)
- Vylepšené `std::list` ladění kontroly. Iterátory nyní zkontrolujte seznam `operator->()`, a `list::unique()` nyní označí iterátory jako zneplatněny.
- Oprava používá allocator metaprogramování v `tuple`.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- `std::partition` nyní volání časy predikátu N místo N + 1 časy jako standardní vyžaduje.
- Pokusy o statické objekty magic ve verzi 15.3, aby byl opraven ve verzi 15.5.
- `std::atomic<T>` už nevyžaduje `T` jako výchozí constructible.
- Haldy algoritmy, které už logaritmické nespěchejte provést kontrolní výraz lineárním čase, že vstup je ve skutečnosti haldu Pokud je povolená pro iterační ladění.
- `__declspec(allocator)` je teď pro C1XX pouze, aby se zabránilo upozornění Clang, který nerozumí tento declspec chráněné.
- `basic_string::npos` je teď dostupná jako časovou konstantou kompilace.
- `std::allocator` v C ++ 17 režimu je větší než nyní správně zpracovává přidělení nadbytečně zarovnané typy, typy to znamená, jejichž zarovnání `max_align_t`, pokud zakázal **/Zc:alignedNew-** .  Například vektory objektů s 16 bajtů nebo 32 bajtů zarovnání jsou teď správně zarovnané SSE a AVX pokyny.

### <a name="conformance-improvements"></a>Vylepšení shody

- Přidali jsme \<jakékoli\>, \<string_view\>, `apply()`, `make_from_tuple()`.
- Přidání \<volitelné\>, \<variant\>, `shared_ptr::weak_type`, a \<cstdalign\>.
- Povolené C ++ 14 `constexpr` v `min(initializer_list)`, `max(initializer_list)`, a `minmax(initializer_list)`, a `min_element()`, `max_element()`, a `minmax_element()`.

Další informace najdete v tématu [Visual C++ jazykem](../visual-cpp-language-conformance.md).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Několik dalších funkcí C ++ 17 byly implementovány. Další informace najdete v tématu [shoda jazyka Visual C++](cpp-conformance-improvements.md#improvements_153).
- Implementovat P0602R0 "variant a volitelné by měl rozšířit copy/move triviality".
- Standardní knihovna teď oficiálně toleruje dynamické RTTI, protože se zakázalo prostřednictvím [/GR-](../build/reference/gr-enable-run-time-type-information.md) možnost. Obě `dynamic_pointer_cast()` a `rethrow_if_nested()` ze své podstaty vyžadují `dynamic_cast`, takže se označuje jako standardní knihovna teď `=delete` pod **/GR-** .
- I když dynamické RTTI byl zakázán prostřednictvím **/GR-** , "statická" RTTI ve formě `typeid(SomeType)` je stále k dispozici a využívá několik součástí standardní knihovny. Standardní knihovna teď podporuje také zakázáním této funkce přes **/D\_HAS\_statické\_RTTI = 0**. Tento příznak také zakáže `std::any`, `target()` a `target_type()` členské funkce `std::function`a `get_deleter()` členskou funkci friend `std::shared_ptr` a `std::weak_ptr`.
- Standardní knihovna teď používá C ++ 14 `constexpr` bezpodmínečně, namísto podmíněně definovaná makra.
- Standardní knihovna teď používá šablony aliasů interně.
- Standardní knihovna teď používá `nullptr` interně, nikoli z `nullptr_t{}`. (Interní využití NULL byla odstraněna. Interní využití 0 jako null právě prochází čištěním postupně.)
- Standardní knihovna teď používá `std::move()` interně, namísto stylistically zneužití `std::forward()`.
- Změnit `static_assert(false, "message")` k `#error message`. Tato změna zlepšuje diagnostiky kompilátoru, protože `#error` okamžitě přeruší kompilaci.
- Standardní knihovna již označí funkce jako `__declspec(dllimport)`. Moderní linkeru technologií už nevyžaduje ho.
- Extrahované SFINAE pro výchozí argumenty šablony, které snižuje nepořádku v porovnání s návratové typy a typy argumentů funkce.
- Ladění se změnami \<náhodné\> teď použít obvyklé výbavu standardní knihovny, místo vnitřní funkce `_Rng_abort()` kterou volat `fputs()` k **stderr**. Implementace této funkce je se uchovávají po dobu binární kompatibilitu, ale byla odebrána v příští verzi binární nekompatibilní standardní knihovny.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- Některé funkce standardní knihovny byly přidány, zastaralé nebo odebrání v souladu s standardu C ++ 17. Další informace najdete v tématu [ C++ vylepšení v sadě Visual Studio](cpp-conformance-improvements.md#improvements_155).
- Experimentální podporu pro následující paralelní algoritmy:
  - `all_of`
  - `any_of`
  - `for_each`
  - `for_each_n`
  - `none_of`
  - `reduce`
  - `replace`
  - `replace_if`
  - `sort`
- Podpisy pro následující paralelní algoritmy jsou přidána ale neparalelizovaných v tuto chvíli; profilace jsme si ukázali, žádné výhody v paralelním zpracováním algoritmy, které jsou pouze přesunutí nebo permute – elementy:
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

- \<memory_resource >
- Knihovna základy V1
- Odstraňuje se `polymorphic_allocator` přiřazení
- Zlepšení odvození argumentu šablony třídy

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

- Podpora pro paralelní algoritmy, už nejsou experimentální
- novou implementaci \<filesystem >
- základní řetězec převody (částečná podpora)
- `std::launder()`
- `std::byte`
- `hypot(x,y,z)`
- jak se vyhnout zbytečným decay
- speciální matematické funkce
- `constexpr char_traits`
- Průvodce dedukcí pro standardní knihovnu

Další informace najdete v tématu [Visual C++ jazykem](../visual-cpp-language-conformance.md).

### <a name="performance-and-throughput-fixes"></a>Výkon a propustnost opravy

- Provedené `basic_string::find(char)` přetížení pouze volání `traits::find` po. Dříve bylo implementováno jako hledání obecného řetězce pro řetězec o délce 1.
- `basic_string::operator==` Teď kontroluje velikost řetězce před porovnáním obsahů řetězců.
- Odebrali jsme párování v ovládacích `basic_string`, což bylo obtížné optimalizátoru k analýze. U všech krátkých řetězců volání `reserve` má stále nenulové náklady na neprovedení.
- `std::vector` přepracována pro vyšší výkon a správnost: aliasy při vložení a emplace – operace je nyní správně zpracovává jak vyžaduje standard, záruka silné výjimky se teď poskytuje, pokud to vyžaduje Standard prostřednictvím `move_if_noexcept()` a další Logika, Vložit a emplace – provádět méně operací s prvky.
- C++ Standardní knihovna teď předchází přesměrování ukazatelů null.
- Vylepšené `weak_ptr::lock()` výkonu.
- Pro zvýšení propustnosti kompilátoru C++ hlavičky standardní knihovny se deklarace pro nepotřebné vnitřní funkce kompilátoru.
- Vyšší výkon `std::string` a `std::wstring` konstruktorů přesunutí více než třikrát.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Pracoval kolem interakce s `noexcept` která zabránila vkládání `std::atomic` implementace do funkce, které používají strukturované zpracování výjimek (SEH).
- Změněné standardní knihovně poškodilo vnitřní `_Deallocate()` funkce optimalizace na menší kód, což umožňuje být vloženy do více míst.
- Změnit `std::try_lock()` nahrazujícím rekurze rozšíření balíčku.
- Vylepšené `std::lock()` použití algoritmu předcházení zablokování `lock()` operace namísto pokryjte na `try_lock()` na všech zámků.
- Povolené optimalizace pojmenované vrácená hodnota v `system_category::message()`.
- `conjunction` a `disjunction` nyní vytvořit instanci N + 1 typů, aniž 2 n + 2 typy.
- `std::function` už vytvoří instanci stroje podporu alokátoru pro každý typu volatelná aplikacemi, zlepšení propustnosti a snížení velikosti .obj v aplikacích, které předávají mnoho různých výrazy lambda na `std::function`.
- `allocator_traits<std::allocator>` obsahuje ručně vložit `std::allocator` operace, snížení velikosti kódu v kódu, který komunikuje s `std::allocator` prostřednictvím `allocator_traits` pouze (to znamená, že v většinu kódu).
- Volání standardní knihovna teď zpracovává rozhraní C ++ 11 minimálních alokátorů `allocator_traits` přímo, namísto obtékání přidělujícího modulu do interní třídy `_Wrap_alloc`. Tato změna snižuje velikost kód generovaný pro podpory pro allocator, zlepšuje optimalizátoru schopnost argumentovat o kontejnery standardní knihovny v některých případech a poskytuje lepší možnosti ladění (jak je vidět váš typ alokátoru, spíše než `_Wrap_alloc<your_allocator_type>`v ladicím programu).
- Odebrat metaprogramování upravené `allocator::reference`, které alokátorů nejsou povoleny ve skutečnosti k přizpůsobení. (Alokátory: můžete vytvářet kontejnery pomocí ukazatelů, ale ne nápadité odkazy.)
- Front-endu kompilátoru se museli k rozbalení ladění iterátorů v zlepšuje výkon ladění sestavení na základě rozsahu smyček for.
- `basic_string` Interní zmenšení cestu pro `shrink_to_fit()` a `reserve()` již není v cestě přerozdělení operace, snížení velikosti kódu pro všechny členy mutující.
- `basic_string` Interní růst cestu již není v cestě `shrink_to_fit()`.
- `basic_string` Mutující operace jsou nyní promítnout do Rychlá cesta přidělení a přidělení pomalou cestou funkce, díky tomu je vyšší pravděpodobnost pro běžné bez opětovné se nedá vložit do volající.
- `basic_string` Mutace operace nyní konstrukce nevyčerpané vyrovnávací paměti v požadovaném stavu, spíše než změnu velikosti na místě. Například vkládání na začátku řetězce teď přesune obsah po vložení právě jednou (mimo provoz nebo na nově přidělenou vyrovnávací paměť), namísto dvakrát v případě reallocating (nově přidělené vyrovnávací paměti a potom dolů).
- Operace volání standardní knihovny jazyka C v \<řetězec\> nyní do mezipaměti `errno` adresu odebrat opakované interakce s TLS.
- Zjednodušená `is_pointer` implementace.
- Dokončení změn na základě funkce sfinae u výrazů k `struct` a `void_t`– na základě.
- Algoritmy standardní knihovny se postincrementing iterátory.
- Oprava zkrácení upozornění při použití 32-bit alokátorů v 64bitových systémech.
- `std::vector` Přesunutí přiřazení je teď mnohem efektivnější v případě jiných POCMA rovná allocator opětovným použitím vyrovnávací paměti, pokud je to možné.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- `basic_string<char16_t>` Teď provede stejné `memcmp`, `memcpy`a podobné optimalizace, které `basic_string<wchar_t>` zaujme.
- Omezení optimalizace, které brání ukazatelů na funkce nebudou vloženy, vystavené naše práce "vyhnout kopírování funkcí" v sadě Visual Studio 2015 Update 3, byla pracoval, obnovení výkon `lower_bound(iter, iter, function pointer)`.
- Režie pro iterační ladění vaší objednávky ověření vstupy `includes`, `set_difference`, `set_symmetric_difference`, a `set_union` byla snížena rozbalení iterátory před vrácením se změnami pořadí.
- `std::inplace_merge` Nyní přeskočí elementy, které jsou už v umístění.
- Vytváření `std::random_device` už sestaví a potom zničí `std::string`.
- `std::equal` a `std::partition` měl dělení na vlákna jump optimalizace průchodu, který se uloží porovnávání iterátoru.
- Když `std::reverse` ukazatele je předaný pro triviálně kopírovatelné `T`, odešle teď do rukou psaný vektorizovaných implementace.
- `std::fill`, `std::equal`, a `std::lexicographical_compare` byly museli jak provést odeslání `memset` a `memcmp` pro `std::byte` a `gsl::byte` (a ostatní char jako výčty a výčet tříd). Protože `std::copy` odešle zprávu pomocí `is_trivially_copyable`, je to nebylo potřeba žádné změny.
- Standardní knihovna již nebude obsahovat žádné prázdné závorky destruktory, jehož jediným chování bylo zajistit typy bez triviálně zničitelné.

## <a name="other-libraries"></a>Další knihovny

### <a name="open-source-library-support"></a>Podpora Open source knihovny

**Vcpkg** je open source nástroj příkazového řádku, který výrazně zjednodušuje proces načítání a sestavování open source C++ statických knihoven a knihovny DLL v sadě Visual Studio. Další informace najdete v tématu [vcpkg: Správce balíčků pro C++](../build/vcpkg.md).

### <a name="cpprest-sdk-290"></a>CPPRest SDK 2.9.0

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

CPPRestSDK multiplatformní webového rozhraní API jazyka C++, byla aktualizována na verzi 2.9.0. Další informace najdete v tématu [CppRestSDK 2.9.0 je k dispozici na Githubu](https://devblogs.microsoft.com/cppblog/cpprestsdk-2-9-0-is-available-on-github/).

### <a name="atl"></a>ATL

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- Ještě další sada oprav neshod vyhledávání názvů
- Existující konstruktory přesunutí a operátory přiřazení jsou teď správně označené jako non-throwing. přesunutí a operátory
- Unsuppress platné upozornění c4640 týkajícího vláknově bezpečné inicializace místních statik v atlstr.h
- Vláknově bezpečné inicializace místních statik byla automaticky vypnuto v sadě nástrojů XP pomocí knihovny ATL pro vytváření knihovny DLL, ale nyní není. Můžete přidat **/Zc: threadsafeinit** v nastavení projektu, pokud se požaduje s bezpečným pro vlákno inicializace.

### <a name="visual-c-runtime"></a>Modul runtime Visual C++

- Nové záhlaví "cfguard.h" pro symboly ochrany toku provádění.

## <a name="c-ide"></a>C++ IDE

- Výkon při změně konfigurace je teď vyšší u nativních projektů C++ a mnohem vyšší u projektů C++/CLI. Pokud se konfigurace řešení aktivuje poprvé, bude nyní rychleji a všechny novější aktivace této konfigurace řešení budou prakticky okamžité.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Několik průvodců projektu a kódu je přepsaných ve stylu dialogu podpisu.
- **Přidejte třídu** teď přímo spustí průvodce Přidat třídu. Všechny ostatní položky, které byly dříve tady, jsou teď k dispozici v rámci **Přidat > Nová položka**.
- Projekty Win32 jsou teď v **Windows Desktop** kategorii **nový projekt** dialogového okna.
- **Konzoly Windows** a **aplikace klasické pracovní plochy** šablony teď vytvoří projekty bez zobrazení průvodce. Je tu nový **desktopový Průvodce pro Windows** v rámci stejné kategorie, která zobrazí stejné možnosti jako původní **Konzolová aplikace Win32** průvodce.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

Několik operací v jazyce C++, které používají modul IntelliSense pro refaktoring a navigace v kódu spusťte mnohem rychleji. Tato čísla jsou založeny na Visual Studio chromu řešení s projekty 3500:

|||
|-|-|
|Funkce|Zlepšení výkonu|
|přejmenování|5.3 x|
|Změnit signaturu |4.5 x|
|Najít všechny odkazy|4.7 x|

Jazyk C++ nyní podporuje Ctrl + kliknutí **přejít k definici**, usnadňuje navigace myši do definic. Vizualizér struktur z této sady nástrojů Productivity Power Tools je nyní také součástí produktu ve výchozím nastavení.

## <a name="intellisense"></a>IntelliSense

- Ve výchozím nastavení je nyní používán nový databázový stroj využívající SQLite. Tím se urychlí databázové operace jako **přejít k definici** a **najít všechny odkazy**a výrazně se zkrátí doba analýzy počátečního řešení. Nastavení se přesunulo do **nástroje > Možnosti > textový Editor > C/C++ > Upřesnit** (dříve bylo pod... C/C++ | Experimentální).

- Vylepšili jsme výkon technologie IntelliSense v projektech a souborech, které nepoužívají předkompilované hlavičky – pro hlavičky aktuálního souboru se vytvoří Automatická Předkompilovaná hlavička.

- Přidali jsme do seznamu chyb filtrování a nápovědu k chybám technologie IntelliSense. Kliknutí na sloupec s chybami teď umožní je filtrovat. Kromě toho kliknutím na konkrétní chyby nebo stisknutím klávesy F1 spustíte online vyhledávání chybové zprávy.

  ![Seznam chyb](media/ErrorList1.png "Seznam chyb")

  ![Filtrovaný seznam chyb](media/ErrorList2.png "Filtrovaný seznam chyb")

- Přidali jsme možnost filtrovat položky seznamu členů podle typu.

  ![Filtrování seznamu členů](media/mlfiltering.png "Filtrování seznamu členů")

- Přidat novou experimentální funkci prediktivní IntelliSense, který poskytuje přizpůsobené závislé filtrování toho, co se zobrazuje v seznamu členů. Další informace najdete v tématu [ C++ vylepšení IntelliSense – prediktivní IntelliSense a filtrování](https://devblogs.microsoft.com/cppblog/c-intellisense-improvements-predictive-intellisense-filtering/).
- **Najít všechny odkazy** (Shift + F12) teď pomáhá vám snadno dostanete, i v komplexních základů kódu. Poskytuje pokročilé seskupování, filtrování, řazení, hledání v rámci výsledků a (pro některé jazyky) zabarvení, abyste se mohli pochopili, že vaše odkazy. Pro C++, nové uživatelské rozhraní obsahuje informace o tom, jestli jsme se čtení nebo zápisu proměnné.
- Funkce změny tečky na šipku technologie IntelliSense se změnila z experimentální na pokročilou a teď je ve výchozím nastavení povolená. Funkce editoru **rozbalení oborů** a **rozbalení priorit** také byly přesunuté z experimentálních na Pokročilé.
- Funkce experimentálního refaktoringu **změnit signaturu** a **extrahovat funkci** jsou teď dostupné ve výchozím nastavení.
- Přidá experimentální funkce "Rychleji projektu zatížení" pro C++ projekty. Při příštím otevření C++ projektu zavede se rychleji a čas, po se načtou aby *většinu* rychleji!
- Některé z těchto funkcí jsou společné pro ostatní jazyky a některé jsou specifické pro C++. Další informace o těchto nových funkcích najdete v tématu [oznamujeme vydání sady Visual Studio "15" Preview 5](https://devblogs.microsoft.com/visualstudio/announcing-visual-studio-15-preview-5/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

- Byla přidána podpora pro ClangFormat. Další informace najdete v tématu [podporu pro ClangFormat v sadě Visual Studio 2017](https://devblogs.microsoft.com/cppblog/clangformat-support-in-visual-studio-2017-15-7-preview-1/).

## <a name="non-msbuild-projects-with-open-folder"></a>Projekty MSBuild bez pomocí otevřít složku

Visual Studio 2017 zavádí **otevřít složku** funkci, která umožňuje kód, vytvářet a ladit ve složce obsahující zdrojový kód bez nutnosti vytvářet jakékoli řešení nebo projektů. Nyní je mnohem jednodušší, abyste mohli začít se sadou Visual Studio, i v případě, že váš projekt není projekt aplikace založené na MSBuild. S **otevřít složku**, získáte přístup k výkonné kódu principy, úpravy, sestavování a ladění funkcí, které již poskytuje Visual Studio pro projekty MSBuild. Další informace najdete v tématu [projekty otevřít složku pro jazyk C++](../build/open-folder-projects-cpp.md).

- Vylepšení prostředí Otevřít složku Přizpůsobte si prostředí pomocí tyto soubory .json:
  - CppProperties.json použijte k přizpůsobení technologie IntelliSense a prostředí procházení.
  - Tasks.json použijte k přizpůsobení kroků sestavení.
  - Launch.json použijte k přizpůsobení prostředí ladění.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Vylepšená podpora pro alternativní kompilátory a prostředí sestavení, jako je například MinGW a Cygwin. Další informace najdete v tématu [pomocí MinGW a Cygwin pomocí jazyka Visual C++ a otevřít složku](https://devblogs.microsoft.com/cppblog/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/).
- Byla přidána podpora pro definování proměnných prostředí určených pro konfigurace a globální CppProperties.json a CMakeSettings.json. Tyto proměnné prostředí můžete využívat v konfiguracích ladění definovaných v souboru launch.vs.json a úkolech v tasks.vs.json. Další informace najdete v tématu [přizpůsobení prostředí pomocí Visual C++ a otevřít složku](https://devblogs.microsoft.com/cppblog/customizing-your-environment-with-visual-c-and-open-folder/).
- Vylepšená podpora pro generátor Ninja CMake, včetně možnosti snadno cílit na 64bitové platformy.

## <a name="cmake-support-via-open-folder"></a>Podpora CMake prostřednictvím funkce Otevřít složku

Visual Studio 2017 zavádí podporu pro práci s projekty CMake bez nutnosti dalších souborech projektu MSBuild (.vcxproj). Další informace najdete v tématu [projekty CMake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md). Otevírání projektů CMake s **otevřít složku** automaticky nakonfiguruje prostředí pro úpravy, sestavování a ladění C++.

- Technologie IntelliSense jazyka C++ funguje bez nutnosti vytvoření souboru CppProperties.json v kořenové složce. Dále jsme přidali novou rozevírací nabídku, která umožňuje uživatelům snadno přepínat mezi konfiguracemi poskytovanými soubory CMake a CppProperties.json.

- Prostřednictvím souboru CMakeSettings.json, který je umístěný ve stejné složce jako soubor CMakeLists.txt, se podporuje další konfigurace.

  ![Otevřít složku – CMake](media/cmake-cpp.png "Otevřít složku – CMake")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Byla přidána podpora pro generátor CMake Ninja.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- Byla přidána podpora pro import stávající mezipaměti CMake.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- Přidána podpora pro CMake 3.11, analýza kódu v projektech CMake, zobrazení cílů v Průzkumníku řešení, možnosti mezipaměti, kompilaci a generování jednoho souboru. Další informace najdete v tématu [podpora CMake v sadě Visual Studio](https://devblogs.microsoft.com/cppblog/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) a [projekty CMake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md).

## <a name="windows-desktop-development-with-c"></a>Vývoj pro plochu Windows v C++

Při instalaci původní úlohy pro C++ teď poskytujeme podrobnější prostředí instalace. Přidali jsme volitelné součásti, které vám umožní vybrat a nainstalovat jen ty nástroje, které potřebujete. Velikosti uvedené instalace součástí uvedené v instalačním programu uživatelského rozhraní nejsou přesné a podceňují skutečnou celkovou velikost.

Když chcete úspěšně vytvářet projekty Win32 v úloze vývoje desktopových aplikací v C++, musíte nainstalovat sadu nástrojů i sadu Windows SDK. Instalace doporučených (vybraných) komponent **nástrojů pro VC ++ 2017 v141 (x86, x64)** a **Windows 10 SDK (10.0.nnnnn)** k Ujistěte se, že funguje. Pokud nebudou potřebné nástroje nainstalované, projekty se nevytvoří úspěšně a Průvodce přestane reagovat.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

(Dříve dostupné jako samostatný produkt) Visual C++ Build tools jsou nyní zahrnuty jako úloha v instalačním programu sady Visual Studio. Tato úloha se nainstaluje jenom nástroje potřebné k sestavení projektů C++ bez nutnosti instalace integrovaném vývojovém prostředí sady Visual Studio. Sady nástrojů verze 141 i v140 jsou zahrnuty. Sadu nástrojů verze 141 obsahuje nejnovější vylepšení v sadě Visual Studio 2017 verze 15.5. Další informace najdete v tématu [Visual Studio Build Tools nyní zahrnují VS2017 a sady nástrojů MSVC VS2015](https://devblogs.microsoft.com/cppblog/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/).

## <a name="linux-development-with-c"></a>Vývoj pro Linux v C++

Oblíbené rozšíření [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) je teď součástí sady Visual Studio. Tato instalace nabízí všechno, co potřebujete k vývoji a ladění aplikací v jazyce C++, které se spouštějí v prostředí systému Linux.

##### <a name="visual-studio-2017-version-152"></a>Visual Studio 2017 version 15.2

Vylepšení byly provedeny v kódu pro různé platformy pro sdílení obsahu a typu vizualizace. Další informace najdete v tématu [vylepšení Linux C++ pro různé platformy sdílení kódu a typ vizualizace](https://devblogs.microsoft.com/cppblog/linux-cross-platform-and-type-visualization/).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- Přidána podpora pro Linux úloha **rsync** jako alternativu k **sftp** pro synchronizaci souborů do vzdáleného počítače s Linuxem.
- Byla přidána podpora pro různé cílení na ARM mikrokontrolerů po kompilaci. Chcete-li povolit v instalaci, zvolte **vývoj pro Linux v C++**  úlohy a vyberte možnost pro **vložené a IoT vývoj**. Tato možnost přidá kolekce gcc technologie ARM cross tools kompilace a zkontrolujte instalaci. Další informace najdete v tématu [ARM GCC křížové kompilace v sadě Visual Studio](https://devblogs.microsoft.com/cppblog/arm-gcc-cross-compilation-in-visual-studio/).
- Byla přidána podpora pro CMake. Teď můžete pracovat na svém stávajícím základu CMake kódu bez nutnosti převádět na projekt sady Visual Studio. Další informace najdete v tématu [konfigurace projektu Linux CMake](../linux/cmake-linux-project.md).
- Byla přidána podpora pro spouštění vzdálené úlohy. Díky této funkci můžete spouštět jakékoli příkazy ve vzdáleném systému, který je definován v sadě Visual Studio Connection Manager. Vzdálené úlohy také poskytují možnost kopírování souborů do vzdáleného systému.
Další informace najdete v tématu [konfigurace projektu Linux CMake](../linux/cmake-linux-project.md).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

- Různá vylepšení scénáře úloh Linux. Další informace najdete v tématu [úlohy pro C++ Linux vylepšení systém projektu, okna konzoly systému Linux, rsync a připojit k procesu](https://devblogs.microsoft.com/cppblog/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/).
- IntelliSense pro záhlaví na vzdálená připojení Linuxu. Další informace najdete v tématu [technologie IntelliSense pro vzdálených hlaviček Linux](https://devblogs.microsoft.com/cppblog/intellisense-for-remote-linux-headers/) a [konfigurace projektu Linux CMake](../linux/cmake-linux-project.md).

## <a name="game-development-with-c"></a>Vývoj her v C++

Využijte naplno potenciál C++ k vytváření profesionálních her využívajících technologii DirectX nebo Cocos2d.

## <a name="mobile-development-with-c-android-and-ios"></a>Vývoj mobilních aplikací pomocí C++ (Android a iOS)

Mobilní aplikace teď můžete vytvářet a ladit pomocí sady Visual Studio, která se umí zaměřit i na Android a iOS.

## <a name="universal-windows-apps"></a>Univerzální aplikace pro Windows

C++ je volitelnou součástí úlohy Universal Windows App.  Upgrade projektů C++ se v tuto chvíli musí provést ručně. Pokud otevřete projekt cílené v140 univerzální platformu Windows v sadě Visual Studio 2017, musíte na stránkách vlastností projektu vybrat sadu nástrojů verze 141 platformy, pokud nemáte nainstalovanou sadu Visual Studio 2015.

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>Nové možnosti jazyka C++ na univerzální platformu Windows (UPW)

Teď máte nové možnosti pro zápis a balení aplikací pro univerzální platformu Windows a Windows Store v jazyce C++: Přemostění na Desktop infrastruktury můžete zabalit existující aplikace klasické pracovní plochy nebo objekt modelu COM pro nasazení přes Windows Store nebo prostřednictvím stávajících prodejních kanálů prostřednictvím zkušební načtení. Nové funkce ve Windows 10 vám umožňují přidat funkce UPW do aplikace klasické pracovní plochy různými způsoby. Další informace najdete v tématu [přemostění na Desktop](/windows/uwp/porting/desktop-to-uwp-root).

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

A **projekt Windows Application Packaging** šablona projektu se přidá, což výrazně zjednodušuje vytváření balíčků aplikací klasické pracovní plochy pomocí přemostění na Desktop. Je k dispozici v **soubor | Nové | Projekt | Instalaci | Vizuální C++ | Universal Windows Platform**. Další informace najdete v tématu [balíček aplikace pomocí sady Visual Studio (přemostění na Desktop)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

Pokud zapisujete nový kód, můžete nyní použít C++/WinRT, což je standard C++ projekce jazyk prostředí Windows runtime implementována pouze v souborech hlaviček. Umožňuje oba Autor a používání rozhraní API Windows Runtime pomocí jakýkoli standardům kompilátor jazyka C++. C++/ WinRT je navržené pro poskytování C++ vývojářům první třídy přístup k moderní rozhraní Windows API. Další informace najdete v tématu [ C++/WinRT: Moderní C++ prostředí Windows Runtime](https://moderncpp.com/).

V době sestavení 17025 Windows SDK Insider Preview C++/WinRT je součástí sady Windows SDK. Další informace najdete v tématu [ C++/WinRT je nyní zahrnutá sady Windows SDK](https://devblogs.microsoft.com/cppblog/cppwinrt-is-now-included-the-windows-sdk/).

## <a name="clangc2-platform-toolset"></a>Sada nástrojů platformy clang/C2

Sada nástrojů Clang/C2, která se dodává s Visual Studio 2017 teď podporuje **/bigobj** přepnout, což je zásadní pro sestavování rozsáhlých projektů. Zahrnuje také několik důležitých oprav chyb, jak ve front-endu, tak v back-endu kompilátoru.

## <a name="c-code-analysis"></a>Analýza kódu C++

Se sadou Visual Studio se nyní distribuují moduly pro kontrolu jádra C++, které vynucují [pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines). Stačí tyto moduly pro kontrolu v povolit **rozšířeními pro analýzu kódu** stránky v stránky vlastností projektu a rozšíření se zahrnou spouštění analýz kódu. Další informace najdete v tématu [pomocí tyto moduly pro kontrolu podle dokumentu C++ Core Guidelines](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

![CppCoreCheck](media/CppCoreCheck.png "Stránka vlastností CppCoreCheck")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

- Byla přidána podpora pro pravidla týkající se správy prostředků.

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

- Nové C++ Core Guidelines kontroly se týkají správnosti chytrých ukazatelů, správného použití globálních inicializátorů a označování použití konstruktorů, jako je `goto` a chybný přetypování.

- Některá čísla upozornění, která najdete v 15.3, už nejsou k dispozici v 15.5. Tato upozornění byla nahrazena specifičtějšími kontrolami.

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 verze 15.6

- Byla přidána podpora pro jeden soubor analýzy a vylepšení analýzy výkonu za běhu. Další informace najdete v tématu [vylepšení statické analýzy C++ pro Visual Studio 2017 15.6 Preview 2](https://devblogs.microsoft.com/cppblog/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/)

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

- Podpora pro přidání [/ analyze: ruleset](../build/reference/analyze-code-analysis.md), které lze zadat pravidla analýzy kódu pro spuštění.
- Byla přidána podpora pro další pravidla podle dokumentu C++ Core Guidelines.  Další informace najdete v tématu [pomocí tyto moduly pro kontrolu podle dokumentu C++ Core Guidelines](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

## <a name="unit-testing"></a>Testování jednotek

##### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

Adaptér Google Test a Boost.Test adaptér jsou teď k dispozici jako součásti **Desktop Development with C++** pracovního vytížení a jsou integrované s **Průzkumník testů**. Přidá se CTest podporu pro projekty Cmake (pomocí otevřít složku), i když plnou integraci s **Průzkumník testů** ještě není k dispozici. Další informace najdete v tématu [zápis testů jednotek pro C/C++](/visualstudio/test/writing-unit-tests-for-c-cpp).

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 verze 15.6

- Byla přidána podpora pro Boost.Test podpora dynamických knihoven.
- Šablony položek Boost.Test je teď k dispozici v integrovaném vývojovém prostředí.

Další informace najdete v tématu [Boost.Test testování částí: Dynamická knihovna podpory a nové šablony položky](https://devblogs.microsoft.com/cppblog/boost-test-unit-testing-dynamic-library-support-and-new-item-template/).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

[Funkce CodeLens](/visualstudio/ide/find-code-changes-and-other-history-with-codelens) přidány pro podporu C++ projektů testů jednotek. Další informace najdete v tématu [uvedení funkce CodeLens pro testování částí C++](https://devblogs.microsoft.com/cppblog/announcing-codelens-for-c-unit-testing/).

## <a name="visual-studio-graphics-diagnostics"></a>Diagnostika grafiky sady Visual Studio

Diagnostika grafiky sady Visual Studio je sada nástrojů pro zaznamenávání a analýzu problémů vykreslování a výkon v aplikacích rozhraní Direct3D. Funkce diagnostiky grafiky můžete použít s aplikacemi, které běží místně v počítači Windows v emulátoru zařízení Windows nebo na vzdálený počítač nebo zařízení.

- **Vstup a výstup pro Vertex a Geometry Shader:** Jedna z nejžádanějších funkcí byla možnost zobrazit vstup a výstup vertex shader a shader geometrie a je nyní podporována v nástrojích. Jednoduše vyberte fázi sady Visual Studio nebo GS v okně fáze zřetězení spustit kontrola vstup a výstup v následující tabulce.

  ![Vstup/výstup pro shadery](media/io-shaders.png)

- **Vyhledávání a filtrování v tabulce objektů:** Poskytuje rychlý a snadný způsob, jak najít prostředky, které hledáte.

  ![Hledat](media/search.png)

- **Historie prostředku:** Toto nové zobrazení poskytuje efektivní způsob, jak zobrazuje historii celý úpravy prostředku, jako jste použili při vykreslování zachyceného snímku. Abyste mohli vyvolat historie pro libovolné prostředky, stačí klikněte na ikonu hodin vedle libovolný prostředek hypertextový odkaz.

  ![Historie prostředku](media/resource-history.png)

  Zobrazí se nové **rie prostředku** oknem nástrojů, vyplní historii změn prostředku.

  ![Historie změn prostředků](media/resource-history-change.png)

  Pokud byla zaznamenána rámce s úplnou volání zásobníku zachytávání povolené (**sady Visual Studio > Nástroje > Možnosti** pod **diagnostiky grafiky**), potom kontext každou událost změny je možné rychle odvodit a zkontroloval v rámci projektu sady Visual Studio.

- **Statistika API:** Zobrazte podrobný souhrn využití rozhraní API v rámce. Je užitečné pro zjištění, že volání že nemusí zjistíte, které vytváříte vůbec nebo volání, které vytvoříte příliš mnoho. Toto okno je k dispozici prostřednictvím **zobrazení > Statistika API** v analyzátoru grafiky sady Visual Studio.

  ![Statistika API](media/api-stats.png)

- **Statistika paměti:** Zobrazte, kolik paměti je ovladač přidělování prostředků vytvoříte v rámci. Toto okno je k dispozici prostřednictvím **zobrazení > Statistika paměti** v **analyzátoru grafiky sady Visual Studio**. Data je možné zkopírovat do souboru CSV pro zobrazení v tabulce tak, že kliknete pravým tlačítkem a zvolíte **Kopírovat vše**.

  ![Statistika paměti](media/memory-stats.png)

- **Ověření snímku:** Nový seznam chyb a upozornění poskytuje snadný způsob, jak přejít seznamu událostí podle potenciálních problémů zjištěných vrstvu debug Direct3D. Klikněte na tlačítko **zobrazení > ověření snímku** ve Visual Studio Graphics Analyzer otevření okna. Pak klikněte na tlačítko **spustit ověření** spustit analýzu. Může trvat několik minut v závislosti na složitosti rámce.

  ![Ověření snímku](media/frame-validation.png)

- **Analýza snímků pro D3D12:** Analýzu snímků použijte k analýze výkonu volání draw s pokusy řízené "co kdyby". Přepněte na kartu analýza snímků a spuštění analýzy zobrazíte sestavu. Další informace, podívejte se [GoingNative 25: Analýza grafických snímků Visual Studio](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) videa.

  ![Analýza snímků](media/frame-analysis.png)

- **Vylepšení využití GPU:** Otevřít trasování lze provést prostřednictvím využití GPU Visual Studio profiler GPU zobrazení nebo nástroji Windows Performance Analyzer (WPA) pro podrobnější analýzu. Pokud je nainstalovaná sada Windows Performance Toolkit, existují dvě hypertextové odkazy, jednu pro WPA a druhou pro zobrazení GPU v pravém dolním rohu přehledu relace.

  ![Využití GPU](media/gpu-usage.png)

  Otevřít v zobrazení GPU prostřednictvím tohoto odkazu podpory trasování synchronizované přibližování a posouvání na časové ose mezi VS a zobrazení GPU. Zaškrtávací políčko v sadě Visual Studio je slouží ke kontrole, jestli je povolená synchronizace, nebo ne.

  ![Zobrazení GPU](media/gpu-view.png)

::: moniker-end

::: moniker range="=vs-2015"

Úplný seznam novinek prostřednictvím Visual Studio 2015 Update 3 najdete v tématu [Visual C++ co je nového 2003 do 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015). Další informace o novinkách ve všech sady Visual Studio 2015, najdete v článku zpráva k vydání verze, které jsou odkazované z [historie Visual Studio 2015 Release Notes](/visualstudio/releasenotes/vs2015-version-history). Informace o tom, co je nového pro C++ v aplikaci Visual Studio 2019, naleznete v tématu [co je nového pro C++ v sadě Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019). Informace o tom, co je nového pro C++ v sadě Visual Studio 2017, najdete v článku [co je nového pro C++ v sadě Visual Studio 2017](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017).

::: moniker-end
