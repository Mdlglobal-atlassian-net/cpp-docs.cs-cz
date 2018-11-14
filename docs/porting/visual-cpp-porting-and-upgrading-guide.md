---
title: Průvodce přenosem a upgradováním Visual C++
ms.date: 09/18/2018
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
ms.openlocfilehash: 39b0e716ae6dbc1210130908b27cfa1d06f86ec6
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556865"
---
# <a name="visual-c-porting-and-upgrading-guide"></a>Průvodce přenosem a upgradováním Visual C++

Toto téma poskytuje návod pro upgrade kódu jazyka Visual C++. To zahrnuje získání kódu zkompilovat a spustit správně na novější verzi nástrojů, jakož i využívat nový jazyk a funkce aplikace Visual Studio. Toto téma obsahuje také informace o migraci starších aplikací na Modernější platformy.

## <a name="reasons-to-upgrade-visual-c-code"></a>Důvody pro Upgrade kódu Visual C++

Měli byste zvážit upgrade kódu z následujících důvodů:

- Rychlejší kód z důvodu vylepšení kompilátoru optimalizace.

- Rychlejší sestavování, kvůli zvýšení výkonu kompilátoru samotný.

- Shoda se standardy lepší. Visual C++ teď implementuje mnoho funkcí z nejnovějších standardů C++.

- Lepší zabezpečení. Funkce zabezpečení, jako je kontroluje.

### <a name="porting-your-code"></a>Portování kódu

Při upgradu, nejprve zvažte kódu vaší aplikace a projekty. Je vaše aplikace vytvořená pomocí sady Visual Studio? Pokud ano, identifikujte projekty, které jsou zahrnuté.  Máte skripty vlastního sestavení? Pokud máte skripty vlastního sestavení místo sestavení systému Visual Studio, budete mít další práci v rámci upgradu, protože nelze ušetřit čas tím, že Visual Studio, aktualizujte si soubory projektu a nastavení sestavení.

Formát sestavení projekt a systému souborů v sadě Visual Studio se změní z vcbuild ve verzích až Visual Studio 2008 na MSBuild verze sady Visual Studio 2010 a vyšší. Pokud se upgrade z verze před 2010 a máte vysoce přizpůsobenou systém, bude pravděpodobně více práce k upgradu. Pokud jste upgrade z produktu Visual Studio 2010 nebo novější, vaše projekty upgrade projektu a sestavení pro vaši aplikaci, by tak měly být jednodušší už používáte MSBuild.

Pokud nepoužíváte systém sestavení sady Visual Studio, měli byste zvážit upgrade na použití nástroje MSBuild. Pokud upgradujete na použití nástroje MSBuild, bude pravděpodobně usnadní v budoucí inovace a bude usnadňuje používání služeb, jako je Visual Studio Online. Nástroj MSBuild podporuje všechny cílové platformy, které podporuje Visual Studio.

### <a name="porting-visual-studio-projects"></a>Portování projektů sady Visual Studio

Spustit upgrade projektu nebo řešení, právě otevřete řešení v nové verzi sady Visual Studio a postupujte podle výzev a spusťte upgrade se.  Když upgradujete projekt, získáte upgradu sestava, která se také uloží do složky projektu jako UpgradeLog.htm. Upgrade sestava zobrazuje souhrn jaké problémy se vyskytly během procesu upgradu a některé informace o změny, které byly provedeny nebo problémy, které nelze vyřešit automaticky.

1. Vlastnosti projektu

2. Soubory k zahrnutí

3. Kód, který už zkompiluje čistě kvůli imrovements shoda kompilátoru nebo standard se změnami

4. Kód, který využívá funkce sady Visual Studio nebo Windows, které už nejsou k dispozici nebo hlavičkové soubory, které nejsou zahrnuté ve výchozí instalaci sady Visual Studio, nebo byly odebrány z produktu

5. Kód, který již nezkompiluje z důvodu změn v rozhraní API, jako přejmenovat rozhraní API, podpisech funkcí změny a zastaralé funkce

6. Kód, který již nezkompiluje z důvodu změn v diagnostice, jako je například upozornění stávají chybu

7. Linker chyby vzniklé v důsledku knihovny, které byly změněny, zejména v případě, že se používá parametr/NODEFAULTLIB.

8. Chyby za běhu nebo neočekávané výsledky díky změnám chování

9. Chyby vzniklé v důsledku chyby, které byly zavedeny v nástrojích. Pokud narazíte na problém, ohlásit týmu Visual C++ pomocí pracovníkům podpory normální, nebo pomocí [Visual Studio Feedback Center](http://connect.microsoft.com/VisualStudio/Feedback).

Kromě změn, které není možné vyhnout se z důvodu chyb kompilátoru některé změny jsou volitelné v upgradu, jako například:

1. Nová upozornění může znamenat, že chcete vyčistit váš kód. V závislosti na konkrétní diagnostické to zlepšit přenositelnost, shoda se standardy a zabezpečení vašeho kódu.

2. Můžete chtít využívat novější funkce kompilátoru, jako [(povolení toku řízení ochrany) / Guard: CF](../build/reference/guard-enable-control-flow-guard.md) – možnost kompilátoru, který přidává kontroly pro provádění neoprávněný kód.

3. Může vyžadovat aktualizaci kódu pro použití nových funkcí jazyka, které zjednodušuje kód, zvýšit výkon svých programů nebo aktualizovat kód v souladu s moderních standardů a osvědčených postupů a používat moderní knihovny.

Po upgradu a testování projektu, může být také vhodné zvažte vylepšení další kód nebo plánovat budoucí směr kódu nebo dokonce zvažte architekturu vašeho projektu. Obdrží jeho aktuálnímu vývoji? Stane se důležité pro váš kód pro spuštění na jiných platformách?  Pokud ano, jaké platformy?  C++ je standardizovaná jazyk určený přenositelnost a vývoj pro různé platformy v úvahu a ještě kód pro spoustu aplikací na Windows silnou vazbu na platformu Windows. Opravdu chcete Refaktorovat kód, k tomu oddělit tyto součásti, které jsou více svázané na platformu Windows?

A co uživatelského rozhraní? Pokud používáte knihovnu MFC, můžete chtít aktualizovat uživatelské rozhraní. Používáte novější funkce MFC, které byly zavedeny v 2008 jako Feature Pack? Pokud chcete poskytnout novější vzhled a chování vaší aplikace bez přepsání celé aplikace, můžete zvážit použití rozhraní API na pásu karet v prostředí MFC, nebo pomocí některé z nových funkcí knihovny MFC.

Pokud chcete svůj program poskytnout uživatelské rozhraní XAML, ale nechtějí vytvářet aplikace pro UPW, můžete použít C# s WPF vytvořit vrstvě uživatelského rozhraní a Refaktorujte logiky standard C++ do knihoven DLL. Vytvoření vrstvy vzájemná funkční spolupráce v jazyce C + +/ CLI pro připojení k C# pomocí nativního kódu. Další možností je vytvořit aplikaci UPW pomocí [C + +/ CX](https://msdn.microsoft.com/library/windows/apps/xaml/hh699871.aspx) nebo [C + +/ WinRT](https://github.com/microsoft/cppwinrt). Ve Windows 10, můžete použít [Desktop App Converter](https://msdn.microsoft.com/windows/uwp/porting/desktop-to-uwp-run-desktop-app-converter) chcete zabalit desktopové aplikace jako aplikace pro UPW bez nutnosti upravit veškerý kód.

Případně třeba Teď máte nové požadavky nebo můžou předvídat potřebu cílení na jiných platformách než Windows desktop, jako jsou Windows Phone nebo zařízení s Androidem. Může přeneste kód uživatelského rozhraní pro multiplatformní knihovna uživatelského rozhraní. Tyto architektury uživatelského rozhraní můžete cílit na více zařízení a dál používat Visual Studio a ladicím programu sady Visual Studio jako vývojové prostředí.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Upgrade projektů z dřívějších verzí Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|Popisuje, jak používat projekty vytvořené v dřívějších verzích Visual C++.|
|[Co je nového pro kompilátor jazyka C++ v sadě Visual Studio 2017 RC](../what-s-new-for-visual-cpp-in-visual-studio.md)|Změny v prostředí IDE a nástroje z Visual Studia 2015 do sady Visual Studio 2017|
|[Vylepšení shody C++ se sadou Visual Studio 2017](../cpp-conformance-improvements-2017.md)|Vylepšení ze sady Visual Studio 2015 do sady Visual Studio 2017|
|[Historie změn Visual C++ 2003–2015](visual-cpp-change-history-2003-2015.md)|Seznam všech změn v Visual C++ knihovny a nástroje sestavení ze sady Visual Studio 2003 do 2015, které mohou vyžadovat změny v kódu.|
|[Novinky Visual C++ 2003–2015](visual-cpp-what-s-new-2003-through-2015.md)|Všechny "Novinky" informace pro jazyk Visual C++ ze sady Visual Studio 2003 do Visual Studio 2015.|
|[Přenos knihoven třetích stran](porting-third-party-libraries.md)|Jak používat **vcpkg** nástroj příkazového řádku k portu starší knihovny open-source verze kompilován s novější sady nástrojů Visual C++.|
|[Přenos a upgrade: Příklady a případové studie](porting-and-upgrading-examples-and-case-studies.md)|Pro tento oddíl přenáší a upgraduje několik ukázek a aplikací jsme probírali prostředí a výsledky. Můžete zjistit, že čtení těchto poskytuje vás o tom, co se tak zapojí v portování a upgradování procesu. Během tohoto procesu jsme popisují tipy a triky pro upgrade a zobrazit jak se konkrétní chyby byly opraveny.|
|[Přenos aplikací do platformy Universal Windows](porting-to-the-universal-windows-platform-cpp.md)|Obsahuje informace o převodu kódu pro Windows 10|
|[Úvod do prostředí Visual C++ pro uživatele systému UNIX](introduction-to-visual-cpp-for-unix-users.md)|Poskytuje informace pro uživatele systému UNIX, kteří začínají s Visual C++ a chcete se s ním být produktivní.|
|[Přenos ze systému UNIX do Win32](porting-from-unix-to-win32.md)|Tento článek popisuje možnosti pro migraci systému UNIX aplikací pro Windows.|

## <a name="see-also"></a>Viz také

[Visual C++](../visual-cpp-in-visual-studio.md)
