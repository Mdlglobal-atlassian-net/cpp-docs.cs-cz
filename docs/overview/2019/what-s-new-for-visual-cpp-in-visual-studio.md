---
title: Co je nového v C++ ve Visual Studio 2019
ms.date: 04/02/2019
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 493b96a8ce3359cc18287adbae8cbd6c374671ec
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779485"
---
<!--NOTE all https:// links to docs.microsoft.com need to be converted to site-relative links prior to publishing-->

# <a name="whats-new-for-c-in-visual-studio-2019"></a>Co je nového v C++ ve Visual Studio 2019

Visual Studio 2019 přináší řadu vylepšení a oprav prostředí Microsoft C++. Jsme opravy mnoha chyb a nahlášených problémů v kompilátoru a nástrojů, řadu z nich odeslali zákazníci přes [nahlásit problém](/visualstudio/how-to-report-a-problem-with-visual-studio-2017) a [poslat návrh](https://developercommunity.visualstudio.com/spaces/62/index.html) možnosti v části **odeslat zpětnou vazbu**. Děkujeme vám, že hlásíte chyby! Další informace o tom, co je nového v celé sady Visual Studio, navštivte web [co je nového v sadě Visual Studio](/visualstudio/ide/whats-new-visual-studio-2019).

## <a name="c-compiler"></a>kompilátor C++

- `/std:c++latest` Možnost nyní zahrnuje funkce C ++ 20, které nejsou nutně dokončeny, včetně počáteční podporu pro C ++ 20 operátor <> = ("kosmické lodě") pro třícestné porovnání.

- [P0941R2 – makra testu funkcí](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0941r2.html) je kompletní s podporou `__has_cpp_attribute`. Makra testu funkcí jsou podporovány ve všech režimech Standard.

- [C ++ 20 P1008R1 – zákaz agregace s uživatelem deklarované konstruktory](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1008r1.pdf) je kompletní.

- Vylepšená podpora pro funkce C ++ 17, plus experimentální podporu pro C ++ 20 funkcí jako jsou moduly a korutin. Podrobné informace najdete v tématu [vylepšení shody C++ ve Visual Studio 2019](../cpp-conformance-improvements.md).

- Přepínač kompilátoru jazyka C++ `/Gm` je nyní zastaralá. Zvažte zakázání `/Gm` přepnout ve skriptech sestavení, pokud není výslovně uveden. Ale můžete taky ignorovat upozornění zastarání pro `/Gm`, protože není považováno za chybu při použití "Zpracovávat upozornění jako chyby" (`/WX`).

- U aplikací C++ pro konzoly a klasickou pracovní plochu se už negenerují předkompilované hlavičky.

### <a name="codegen-security-diagnostics-and-versioning"></a>CODEGEN, zabezpečení, Diagnostika a správa verzí

Vylepšení analýzy s `/Qspectre` pro poskytování pomoci zmírnění chyby zabezpečení Spectre Variant 1 (CVE-2017-5753). Další informace najdete v tématu [zmírnění hrozby Spectre v MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/).

## <a name="c-standard-library-improvements"></a>Vylepšení standardní knihovny C++

- [C++ 20 P0550R2 \(remove_cvref)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf) je dokončena.

- C ++ 17 \<charconv > vylepšili jsme plovoucí desetinné čárky to_chars(): nejkratší chars_format::fixed je 60 80 % rychlejší a dokončení chars_format::hex nejkratší nebo přesnosti.

- Další algoritmy mají paralelizovaná implementace: is_sorted() is_sorted_until(), is_partitioned(), set_difference(), set_intersection(), is_heap(), is_heap_until().

- Vylepšení `std::variant` provádět více optimalizace zařízení, což vede k lepší generovaného kódu. Vkládání kódu je teď mnohem lepší s `std::visit`.

- Použili jsme clang-format u hlavičky standardní knihovny C++ pro lepší čitelnost.

- Zlepšení propustnosti při několika funkce standardní knihovny jsou kompilovány pomocí `if constexpr`.

- Optimalizované návrh fyzické standardní knihovny nechcete-li kompilaci není součástí standardní knihovny # include 'D, cutting za poloviční dobu sestavení prázdný soubor, který obsahuje pouze \<vektoru >.

## <a name="performancethroughput-fixes"></a>Výkon/propustnost opravy

- Zlepšení propustnosti, včetně tak, jak linker zpracovává vstup a výstup souborů, ale taky popustit doby v souboru PDB typu slučování a vytvoření propojení.

- Přidání základní podpora pro OpenMP SIMD vektorizaci. Můžete povolit pomocí nového přepínače CL `-openmp:experimental`. Tato možnost umožňuje smyčky opatřen poznámkou `#pragma omp simd` k potenciálně vektorizována. Není zaručeno, vektorizace a smyčky s poznámkami, ale není vektorizována se zobrazí upozornění ohlásil. Bez klauzule SIMD podporují, se jednoduše ignoruje s upozorněním ohlásil.

- Přidat nový přepínač příkazového řádku vkládání `-Ob3`, což je mnohem vyššími verzi `-Ob2`. `-O2` (optimalizovat binární soubor pro rychlost) stále zahrnuje `-Ob2` ve výchozím nastavení. Pokud zjistíte, že kompilátor nebude vložené dostatečně agresivně, zvažte možnost předávání `-O2 -Ob3`.

- Pro podporu ručně vektorizaci smyčky s voláními matematických knihovních funkcí a určité operace jako dělení celého čísla, přidali jsme podporu pro vnitřní funkce krátkého vektoru matematické knihovny (SVML). Tyto funkce compute ekvivalenty vektoru 128-bit, bitů na 256 nebo 512 bitů. Definice podporovaných funkcí najdete v příručce [Intel Intrinsic Guide](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML).

- Nové a vylepšené optimalizace:

  - Konstanta skládání a aritmetické zjednodušení pro výrazy pomocí vnitřní funkce vektoru SIMD, pro plovoucí desetinnou čárkou a celočíselné formuláře.

  - Výkonnější analýzy pro extrahování informací z toku řízení (příkazy if/else/přepínače) Chcete-li odebrat větve vždy prověřené být true nebo false.

  - Vylepšené memset rozvinutí použít SSE2 vektoru.

  - Vylepšené odebrání kopií zbytečné struktury nebo třídy, zejména pro programy v jazyce C++, které předávají podle hodnoty.

  - Vylepšená optimalizace kódu pomocí `memmove`, jako například `std::copy` nebo `std::vector` a `std::string` konstrukce.

## <a name="c-ide"></a>C++ IDE

### <a name="live-share-c-support"></a>Živá podpora C++ sdílené složky

[Live sdílené složky](/visualstudio/liveshare/) teď podporuje C++, což vývojářům, kteří používají Visual Studio nebo Visual Studio Code pro spolupráci v reálném čase. Další informace najdete v tématu [oznámení Live Share jazyka C++: V reálném čase sdílení a spolupráce](https://devblogs.microsoft.com/cppblog/cppliveshare/)

### <a name="intellicode-for-c"></a>IntelliCode jazyka C++

IntelliCode je volitelné rozšíření, které pokud chcete změnit to, co nejpravděpodobněji použijete v horní části seznamu pro doplňování používá vlastní rozsáhlé školení a kontext kódu. Často se může eliminovat potřebu procházejte seznam. Jazyka C++ nabízí IntelliCode většina nápovědy při používání oblíbených knihoven například standardní knihovny. Další informace najdete v tématu [AI-Assisted kódu dokončení návrhy přijdou do C++ prostřednictvím IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/).

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

## <a name="cmake-support"></a>Podpora CMake

- Visual Studio teď můžete otevřít stávající mezipaměti CMake generovaných externí nástroje, jako je například CMakeGUI, systémy meta sestavení nebo skripty sestavení, které vyvolají cmake.exe sami.

- Vylepšený výkon technologie IntelliSense.

- Nový editor nastavení poskytuje alternativu k ruční úpravě souboru CMakeSettings.json a poskytuje některé parity CMakeGUI.

- Visual Studio pomáhá bootstrap, které vaše vývoj v jazyce C++ s CMake v Linuxu pomocí detekce, pokud máte na počítač s Linuxem kompatibilní verzi CMake a pokud ne nabízí aby instalaci udělal za vás.

- V editoru JSON a chyby v seznamu chyb zobrazovat nekompatibilní nastavení v cmakesettings na pozici, například neodpovídající architektury nebo nekompatibilní nastavení generátoru CMake, podtržení vlnovkou.

- Po spuštění příkazu `vcpkg integrate install` se automaticky rozpozná sada nástrojů vcpkg a povolí se pro projekty CMake, které jsou otevřené v integrovaném vývojovém prostředí. Toto chování můžete vypnout tak, že v nástroji CMakeSettings zadáte prázdný soubor sady nástrojů.

- Projekty CMake teď ve výchozím nastavení aktivují ladění s možností Pouze můj kód.

- Upozornění statické analýzy u projektů CMake teď můžete zpracovat na pozadí a zobrazit v editoru.

- Podřazenými vytvořit a konfigurovat zprávy "begin" a "end" pro projekty CMake a podporu pro průběh sestavení sady Visual Studio uživatelského rozhraní. Kromě toho je teď k dispozici CMake podrobností nastavení **nástroje > Možnosti** přizpůsobení úroveň podrobností CMake sestavení a konfiguraci zprávy v okně výstup.

- `cmakeToolchain` Nastavení je nyní podporována v souboru CMakeSettings.json k určení sady nástrojů bez ruční úpravy CMake příkazového řádku.

- Nový **sestavení všechny** zástupce v nabídce **Ctrl + Shift + B**.

## <a name="debugging"></a>Ladění

- Pro aplikace C++ běžící na Windows soubory PDB nyní načíst v samostatném procesu 64-bit. Tato změna řeší celou řadu chyb způsobených ladicí program spuštěn nedostatek paměti při ladění aplikace, které obsahují velký počet modulů a soubory PDB.

## <a name="windows-desktop-development-with-c"></a>Vývoj pro plochu Windows v C++

- Už nejsou k dispozici průvodců C++ knihovny ATL/MFC:

  - Průvodce komponentami 1.0 knihovny ATL modelu COM +
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

- Nová experimentální atribut ConcurrencyCheck pravidla pro známé typy standardní knihovny z \<vzájemně vyloučený přístup > záhlaví. Další informace najdete v tématu [souběžného zpracování analýzy kódu v aplikaci Visual Studio 2019](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/).

- Aktualizované částečnou implementaci [požadovaných součástí profilu životnost](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/), který zjistí nepropojená ukazatele a reference. Další informace najdete v tématu [životního cyklu aktualizace profilu v sadě Visual Studio. 2019 ve verzi Preview 2](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/).

- Další související korutina kontrol, včetně C26138, C26810, C26811 a experimentální pravidlo C26800. Další informace najdete v tématu [nový kód analýzy kontroluje v aplikaci Visual Studio 2019: použití po přesunutí a pomocné rutiny](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/).

## <a name="unit-testing"></a>Testování jednotek

Šablona spravovaného testovacího projektu C++ už není dostupná. Můžete pokračovat v používání rozhraní pro testování spravovaných C++ ve svých existujících projektech. Pro nové jednotkové testy, zvažte použití jedné nativní testovacích platforem, pro které sada Visual Studio obsahuje šablony (MSTest, Google Test) nebo spravované C# šablona projektu pro Test.
