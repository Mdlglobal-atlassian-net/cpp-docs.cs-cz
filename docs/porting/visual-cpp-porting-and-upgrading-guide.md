---
title: Průvodce přenosem a upgradováním Visual C++
ms.date: 09/18/2018
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
ms.openlocfilehash: cd74168419006388b8469086560452a8a99e05e2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511500"
---
# <a name="visual-c-porting-and-upgrading-guide"></a>Průvodce přenosem a upgradováním Visual C++

V tomto tématu najdete pokyny k upgradu vizuálního C++ kódu. To zahrnuje získání kódu pro zkompilování a správné spuštění v novější verzi nástrojů a také využití nových funkcí jazyka a sady Visual Studio. Toto téma obsahuje také informace o migraci starších aplikací na moderní platformy.

## <a name="reasons-to-upgrade-visual-c-code"></a>Důvody k upgradu vizuálního C++ kódu

Měli byste zvážit upgrade kódu z následujících důvodů:

- Rychlejší kód kvůli vylepšeným optimalizacím kompilátoru.

- Rychlejší sestavení kvůli zvýšení výkonu v samotném kompilátoru.

- Vylepšená shoda standardů. Vizuál C++ teď implementuje mnoho funkcí z nejnovějších C++ standardů.

- Lepší zabezpečení. Funkce zabezpečení, jako je kontrola ochrany.

### <a name="porting-your-code"></a>Portování kódu

Při upgradu nejprve zvažte kód a projekty vaší aplikace. Je vaše aplikace sestavená pomocí sady Visual Studio? Pokud ano, identifikujte související projekty.  Máte vlastní skripty sestavení? Máte-li vlastní skripty sestavení namísto použití systému sestavení sady Visual Studio, budete mít více práce při upgradu, protože nemůžete ušetřit čas tím, že aplikace Visual Studio aktualizuje vaše soubory projektu a nastavení sestavení.

Systém sestavení a formát souboru projektu v aplikaci Visual Studio se změnil z nástroje vcbuild ve verzích až do sady Visual Studio 2008 na MSBuild ve verzích sady Visual Studio od 2010 a vyšší. Pokud váš upgrade pochází z verze před 2010 a máte vysoce přizpůsobený systém sestavení, možná budete muset provést další práci, abyste mohli upgradovat. Pokud provádíte upgrade ze sady Visual Studio 2010 nebo novější, projekty již používají nástroj MSBuild, takže upgrade projektu a sestavení pro vaši aplikaci by měl být jednodušší.

Pokud nepoužíváte systém sestavení sady Visual Studio, měli byste zvážit upgrade na použití nástroje MSBuild. Pokud upgradujete nástroj na použití nástroje MSBuild, může být v budoucích upgradech snazší čas a bude snazší používat služby, jako je například Visual Studio Online. Nástroj MSBuild podporuje všechny cílové platformy, které podporuje Visual Studio.

### <a name="porting-visual-studio-projects"></a>Portování projektů sady Visual Studio

Chcete-li zahájit upgrade projektu nebo řešení, stačí otevřít řešení v nové verzi sady Visual Studio a podle pokynů spustit upgrade.  Při upgradu projektu obdržíte zprávu o upgradu, která je také uložena ve složce projektu jako UpgradeLog. htm. Zpráva o upgradu zobrazuje souhrn toho, jaké problémy byly zjištěny během procesu upgradu, a některé informace o provedených změnách nebo problémy, které nebylo možné automaticky řešit.

1. Vlastnosti projektu

2. Zahrnuté soubory

3. Kód, který již není zkompilován čistě z důvodu imrovements shody kompilátoru nebo změn ve standardu

4. Kód, který spoléhá na funkce sady Visual Studio nebo Windows, které již nejsou k dispozici, nebo soubory hlaviček, které buď nejsou zahrnuty ve výchozí instalaci sady Visual Studio, nebo byly z produktu odebrány

5. Kód, který se už nekompiluje kvůli změnám v rozhraních API, jako je přejmenovaná rozhraní API, změněné signatury funkcí nebo zastaralé funkce

6. Kód, který již není zkompilován z důvodu změn v diagnostice, jako je například upozornění chyba

7. Chyby linkeru kvůli změně knihoven, zejména při použití/NODEFAULTLIB.

8. Chyby za běhu nebo neočekávané výsledky z důvodu změn chování

9. Chyby způsobené chybami, které byly představeny v nástrojích. Pokud narazíte na problém, nahlaste ho C++ týmu pomocí běžných kanálů podpory nebo pomocí stránky [komunity vývojářů pro C++ Visual Studio](https://developercommunity.visualstudio.com/spaces/62/index.html) .

Kromě změn, ke kterým se nemůžete kvůli chybám kompilátoru vyhnout, jsou některé změny v procesu upgradu volitelné, například:

1. Nová upozornění mohou znamenat, že chcete vyčistit kód. V závislosti na konkrétní diagnostice to může zlepšit přenositelnost, dodržování standardů a zabezpečení vašeho kódu.

2. Můžete chtít využít výhod novějších funkcí kompilátoru, jako je například [/Guard: CF (Enable Guard Control Guard)](../build/reference/guard-enable-control-flow-guard.md) , které přidávají kontroly pro spuštění neoprávněného kódu.

3. Můžete chtít aktualizovat kód pro použití nových funkcí jazyka, které zjednodušují kód, vylepšit výkon programů nebo aktualizovat kód tak, aby používal moderní knihovny a vyhovovaly moderním standardům a osvědčeným postupům.

Jakmile provedete upgrade a otestování projektu, můžete také zvážit lepší vylepšení kódu nebo naplánování budoucího směru kódu nebo dokonce přehodnocování architektury projektu. Bude docházet k probíhající práci při vývoji? Bude důležité, aby váš kód běžel na jiných platformách?  Pokud ano, jaké platformy?  C++je standardizovaným jazykem navrženým přenositelností a vývojem pro různé platformy, a přesto je kód pro mnoho aplikací pro Windows silně svázaný s platformou Windows. Chcete kód Refaktorovat, aby bylo možné oddělit tyto části, které jsou svázané s platformou Windows?

Jak vaše uživatelské rozhraní? Pokud používáte knihovnu MFC, může být vhodné aktualizovat uživatelské rozhraní. Používáte některou z novějších funkcí MFC, které byly představeny v 2008 jako balíček funkcí? Pokud chcete aplikaci dát k pozdějšímu vzhledu a chování, aniž byste museli psát celou aplikaci, můžete zvážit použití rozhraní API pásu karet v knihovně MFC nebo použití některých nových funkcí knihovny MFC.

Pokud chcete programu poskytnout uživatelské rozhraní XAML, ale nechcete vytvořit aplikaci UWP, můžete použít C# s WPF k vytvoření vrstvy uživatelského rozhraní a Refaktorovat standardní C++ logiku do knihoven DLL. Vytvořte vrstvu interoperability v C++/CLI, abyste C# se připojili k vašemu nativnímu kódu. Další možností je vytvořit aplikaci UWP pomocí systému [ C++/CX](../cppcx/visual-c-language-reference-c-cx.md) nebo [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/). Ve Windows 10 můžete použít [převaděč desktopových aplikací](/windows/msix/desktop/desktop-to-uwp-run-desktop-app-converter) k zabalení stávající desktopové aplikace jako aplikace UWP bez nutnosti upravovat kód.

Případně je možné, že teď máte nové požadavky, nebo můžete předpokládat nutnost cílit na jiné platformy než Windows Desktop, například Windows Phone nebo zařízení s Androidem. Kód uživatelského rozhraní můžete přenést do knihovny uživatelského rozhraní pro různé platformy. S těmito architekturami uživatelského rozhraní můžete cílit na více zařízení a dál používat Visual Studio a ladicí program sady Visual Studio jako vaše vývojové prostředí.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Upgrade projektů z dřívějších verzí Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|Popisuje, jak používat projekty vytvořené v dřívějších verzích sady Visual Studio.|
|[Co je nového pro C++ kompilátor v aplikaci Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)|Změny v rozhraní IDE a nástrojích na aktuální verzi sady Visual Studio|
|[Vylepšení shody C++ se sadou Visual Studio](../overview/cpp-conformance-improvements.md)|Vylepšení shody standardů ze sady Visual Studio 2015 až po Visual Studio|
|[Historie změn Visual C++ 2003–2015](visual-cpp-change-history-2003-2015.md)|Seznam všech změn ve vizuálních C++ knihovnách a nástrojích sestavení ze sady visual Studio 2003 až 2015, které mohou vyžadovat změny v kódu.|
|[Novinky Visual C++ 2003–2015](visual-cpp-what-s-new-2003-through-2015.md)|Všechny informace "Co je nového" pro vizuál C++ ze sady visual Studio 2003 až visual Studio 2015.|
|[Přenos knihoven třetích stran](porting-third-party-libraries.md)|Jak použít nástroj příkazového řádku **vcpkg** pro portování starších Open-Source knihoven do verzí kompilovaných s více nejnovějšími sadami nástrojů vizuálů C++ .|
|[Přenos a upgrade: Příklady a případové studie](porting-and-upgrading-examples-and-case-studies.md)|V této části jsme převedli a upgradují několik ukázek a aplikací a probrali zkušenosti a výsledky. Můžete se setkat s tím, že vám přečtěte, co je součástí procesu přenosu a upgradu. V celém procesu probereme tipy a triky pro upgrade a ukážeme, jak byly vyřešeny konkrétní chyby.|
|[Portování do Univerzální platforma Windows](porting-to-the-universal-windows-platform-cpp.md)|Obsahuje informace o přenosech kódu do Windows 10.|
|[Úvod do prostředí Visual C++ pro uživatele systému UNIX](introduction-to-visual-cpp-for-unix-users.md)|Poskytuje informace pro uživatele systému UNIX, kteří jsou novinkou v jazyce Visual C++ a chtějí s ním být produktivní.|
|[Přenos ze systému UNIX do Win32](porting-from-unix-to-win32.md)|Popisuje možnosti migrace aplikací pro systém UNIX do systému Windows.|

## <a name="see-also"></a>Viz také:

[C++ v sadě Visual Studio](../overview/visual-cpp-in-visual-studio.md)
