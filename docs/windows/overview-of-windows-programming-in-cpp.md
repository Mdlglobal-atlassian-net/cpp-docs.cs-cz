---
title: Přehled programování v C++ v systému Windows
ms.date: 07/28/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: f72e6320493027728a85741ba6d87025454c3b9e
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2019
ms.locfileid: "68607517"
---
# <a name="overview-of-windows-programming-in-c"></a>Přehled programování v C++ v systému Windows

Existuje několik hlavních kategorií aplikací pro Windows, pomocí C++kterých můžete vytvořit. Každá z nich má vlastní programovací model a sadu knihoven specifických pro systém Windows, ale C++ standardní knihovna a knihovny třetích stran C++ lze použít v libovolném z nich. 

Tato část popisuje, jak pomocí sady Visual Studio a knihoven wrapper knihovny MFC/ATL vytvořit programy systému Windows. Dokumentaci k samotné platformě Windows najdete v [dokumentaci k Windows](/windows/index).

## <a name="command-line-console-applications"></a>Aplikace příkazového řádku (konzoly)

C++konzolové aplikace jsou spouštěny z příkazového řádku v okně konzoly a mohou zobrazovat pouze výstupy textu. Další informace najdete v tématu [konzolové aplikace](console-applications-in-visual-cpp.md).

## <a name="native-desktop-client-applications"></a>Nativní klientské aplikace pro stolní počítače

*Nativní klientská aplikace pro stolní počítače* je aplikace C++ v jazyce C nebo okna, která pro přístup k operačnímu systému používá původní nativní rozhraní API pro [Windows c nebo com (Component Object Model)](/windows/desktop/apiindex/windows-api-list) . Tato rozhraní API se sami píší převážně v C. Je k dispozici více než jeden způsob, jak vytvořit nativní desktopovou aplikaci: Můžete programovat přímo pomocí rozhraní Win32 API a použít smyčku zpráv ve stylu jazyka C, která zpracovává události operačního systému. Nebo můžete programovat pomocí knihovny *Microsoft Foundation Classes* (MFC), lehce orientované C++ objektové knihovny, která obaluje Win32. V porovnání s Univerzální platforma Windowsem (UWP) se nepovažuje žádný přístup, ale obě jsou pořád plně podporované a můžou mít miliony řádků kódu běžící na světě ještě dnes. Aplikace Win32, která běží v okně, vyžaduje, aby vývojář pracoval explicitně se zprávami systému Windows v rámci funkce procedury systému Windows. Bez ohledu na název může být aplikace Win32 kompilována jako 32 (x86) nebo 64-bit (x64) binární. V integrovaném vývojovém prostředí sady Visual Studio jsou výrazy x86 a Win32 synonymně.

Chcete-li začít s tradičním programováním v systému Windows C++ , přečtěte si téma Začínáme [s Win32 a C++ ](/windows/desktop/LearnWin32/learn-to-program-for-windows). Až pochopíte prostředí Win32, bude snazší získat informace o [desktopových aplikacích MFC](../mfc/mfc-desktop-applications.md). Příklad tradiční C++ desktopové aplikace, která používá sofistikovanou grafiku, najdete v [tématu Hilo: Vývoj C++ aplikací pro systém](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)Windows.

### <a name="c-or-net"></a>C++nebo .NET?

Obecně platí, že programování .NET C# v nástroji je méně složité, méně náchylné k chybám a má pokročilejší objektově orientované rozhraní API než Win32 nebo MFC. Ve většině případů je jeho výkon více než přiměřený. Rozhraní .NET nabízí Windows Presentation Foundation (WPF) pro bohatou grafiku a můžete využívat Win32 i moderní rozhraní prostředí Windows Runtime API. V rámci obecného pravidla doporučujeme použít C++ pro desktopové aplikace, když budete potřebovat:

- přesná kontrola využití paměti
- nejvyšší ekonomie spotřeby energie
- využití GPU pro obecné výpočty
- přístup k rozhraní DirectX
- těžké použití standardních C++ knihoven

Je také možné kombinovat výkon a efektivitu C++ pomocí programování .NET. V C# nástroji můžete vytvořit uživatelské rozhraní a pomocí C++/CLI povolit aplikaci využívat nativní C++ knihovny. Další informace najdete v tématu [programování .NET s C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="com-components"></a>Komponenty modelu COM

[Component Object Model (com)](/windows/desktop/com/the-component-object-model) je specifikace, která umožňuje programům napsaným v různých jazycích komunikovat mezi sebou. Mnohé součásti systému Windows jsou implementovány jako objekty modelu COM a následují standardní pravidla modelu COM pro vytváření objektů, zjišťování rozhraní a zničení objektů.  Použití objektů COM z C++ desktopových aplikací je relativně jasné, ale psaní vlastního objektu com je pokročilejší. [Knihovna ATL (Active Template Library)](../atl/atl-com-desktop-components.md) poskytuje makra a pomocné funkce, které zjednodušují vývoj v modelu COM. Další informace naleznete v tématu [komponenty ATL com Desktop](../atl/atl-com-desktop-components.md).

## <a name="universal-windows-platform-apps"></a>Universal Windows Platform apps

Univerzální platforma Windows (UWP) je moderní rozhraní Windows API. Aplikace pro UWP běží na jakémkoli zařízení s Windows 10, používají XAML pro uživatelské rozhraní a jsou plně dotykové. Další informace o UWP najdete v tématu [co je aplikace Univerzální platforma Windows (UWP)?](/windows/uwp/get-started/whats-a-uwp) a [Příručka pro univerzální aplikace pro Windows](/windows/uwp/get-started/universal-application-platform-guide).

Původní C++ podpora UWP se skládá z (1) C++/CX, dialektu C++ s rozšířeními syntaxe nebo (2) prostředí Windows Runtime knihovny (WRL), která je založená na standardu C++ a modelu COM. Pro C++/CX i WRL se pořád podporují. Pro nové projekty doporučujeme [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), který je zcela založený na standardu C++ a poskytuje rychlejší výkon.

## <a name="desktop-bridge"></a>Most pro stolní počítače

Ve Windows 10 můžete zabalit stávající desktopovou aplikaci nebo objekt COM jako aplikaci UWP a přidat funkce UWP, jako je dotykové ovládání, nebo volat rozhraní API z moderní sady Windows API. Aplikaci pro UWP můžete také přidat do řešení pro stolní počítače v aplikaci Visual Studio a zabalit je do jednoho balíčku a použít rozhraní API systému Windows ke komunikaci mezi nimi.

Sada Visual Studio 2017 verze 15,4 a novější umožňuje vytvořit projekt balíčku aplikace systému Windows, který výrazně zjednodušuje práci s balíčkem stávající aplikace klasické pracovní plochy. V případě volání registru nebo rozhraní API, které může vaše desktopová aplikace používat, platí několik omezení. V mnoha případech však můžete vytvořit alternativní cesty kódu pro dosažení podobných funkcí při spuštění v balíčku aplikace. Další informace najdete v tématu [most pro stolní počítače](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Videohr

Hry DirectX můžete spustit na počítači nebo Xbox. Další informace najdete v tématu [grafiky a hry DirectX](/windows/desktop/directx).

## <a name="sql-server-database-clients"></a>Klienti databáze SQL Server

Chcete-li získat přístup k SQL Server databází z nativního kódu, použijte rozhraní ODBC nebo OLE DB. Další informace najdete v tématu [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Ovladače zařízení systému Windows

Ovladače jsou komponenty nízké úrovně, které vytvářejí data z hardwarových zařízení přístupných aplikacím a dalším součástem operačního systému. Další informace najdete v tématu [Sada Windows Driver Kit (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>služby systému Windows

*Služba* systému Windows je program, který může běžet na pozadí s malým nebo žádným zásahem uživatele. Tyto programy se nazývají *démoni* v systémech UNIX. Další informace najdete v tématu [služby](/windows/desktop/services/services).

## <a name="sdks-libraries-and-header-files"></a>Sady SDK, knihovny a hlavičkové soubory

Visual Studio zahrnuje knihovnu runtime jazyka C (CRT), C++ standardní knihovnu a další knihovny specifické pro společnost Microsoft. Většina složek zahrnutí, které obsahují hlavičkové soubory pro tyto knihovny, se nachází v instalačním adresáři sady Visual Studio ve složce \VC\. Soubory hlaviček Windows a CRT se nacházejí v instalační složce Windows SDK.

[Správce balíčků Vcpkg](../build/vcpkg.md) vám umožňuje pohodlně nainstalovat stovky Open Source knihoven třetích stran pro Windows.

Mezi knihovny Microsoftu patří:

- Microsoft Foundation Classes (MFC): Objektově orientované rozhraní pro vytváření tradičních programů systému Windows (zejména podnikových aplikací), které mají rozsáhlá uživatelská rozhraní, která tlačítka funkcí, seznamy, stromová zobrazení a další ovládací prvky. Další informace naleznete v tématu [MFC Desktop Applications](../mfc/mfc-desktop-applications.md).

- Knihovna ATL (Active Template Library): Výkonná pomocná knihovna pro vytváření komponent modelu COM. Další informace naleznete v tématu [komponenty ATL com Desktop](../atl/atl-com-desktop-components.md).

- C++AMP (C++ urychlení obrovských paralelismu): Knihovna, která umožňuje vysoce výkonné obecné výpočetní práce na GPU. Další informace najdete v tématu [ C++ amp (C++ urychlení obrovského paralelismu)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Concurrency Runtime: Knihovna, která zjednodušuje práci paralelního a asynchronního programování pro zařízení s více jádry a mnoha jádry. Další informace najdete v tématu [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

Mnoho programovacích scénářů pro Windows navíc také vyžaduje sadu Windows SDK obsahující soubory hlaviček, které umožňují přístup ke komponentám operačního systému Windows. Ve výchozím nastavení Visual Studio nainstaluje Windows SDK jako komponentu pracovní C++ plochy, která umožňuje vývoj univerzálních aplikací pro Windows. Pro vývoj aplikací pro UWP potřebujete Windows SDK verzi Windows 10. Informace najdete v tématu [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk). (Další informace o sadách Windows SDK pro dřívější verze systému Windows najdete v [archivu Windows SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)).

Pro všechny verze Windows SDK, které jste nainstalovali, je výchozí umístění **Program Files (x86)** .

Jiné platformy, jako je například konzola Xbox a Azure mají své vlastní sady SDK, které budete pravděpodobně muset nainstalovat. Další informace naleznete ve středisku pro vývojáře DirectX a ve středisku pro vývojáře Azure.

## <a name="development-tools"></a>Nástroje pro vývoj

Systém Visual Studio obsahuje výkonný ladicí program pro nativní kód, nástroje pro statickou analýzu, nástroje pro ladění grafiky, úplný editor kódu, podporu pro testování částí a mnoho dalších nástrojů a pomůcek. Další informace naleznete v tématu [Začínáme s vývojem v aplikaci Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio)a [Přehled C++ vývoje v aplikaci Visual Studio](../overview/overview-of-cpp-development.md).

## <a name="in-this-section"></a>V tomto oddílu
|Název|Popis|
|-----------|-----------------|
|[Návod: Vytvoření programu ve standardním C++](walkthrough-creating-a-standard-cpp-program-cpp.md)| Vytvořte konzolovou aplikaci pro Windows.|
|[Návod: Vytváření desktopových aplikací Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Vytvořte nativní desktopovou aplikaci pro Windows.|
|[Desktopový průvodce pro Windows](windows-desktop-wizard.md)|K vytvoření nových projektů Windows použijte průvodce.|
|[Knihovna ATL (Active Template Library)](../atl/atl-com-desktop-components.md)|Pomocí knihovny ATL vytvořte komponenty COM v C++.|
|[Knihovna MFC (Microsoft Foundation Classes)](../mfc/mfc-desktop-applications.md)|Použití MFC k vytváření velkých nebo malých aplikací pro Windows s dialogy a ovládacími prvky|
|[Sdílené třídy knihoven ATL a MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)|Používejte třídy, jako je například CString, které jsou sdíleny v ATL a MFC.|
|[Přístup k datům](../data/data-access-in-cpp.md)| OLE DB a rozhraní ODBC|
|[Text a řetězce](../text/text-and-strings-in-visual-cpp.md)|Různé typy řetězců v systému Windows.|
|[Prostředky pro vytvoření hry s použitím rozhraní DirectX](resources-for-creating-a-game-using-directx.md)
|[Postupy: Použití sady Windows 10 SDK v desktopové aplikaci Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows SDK|
|[Práce se zdrojovými soubory](working-with-resource-files.md)|Postup přidání obrázků, ikon, tabulek řetězců a dalších prostředků do aplikace klasické pracovní plochy.|
|[Prostředky pro vytvoření hry s použitím rozhraní DirectXC++()](resources-for-creating-a-game-using-directx.md)|Obsahuje odkazy na obsah pro vytváření her C++v nástroji.|
|[Postupy: Použití sady Windows 10 SDK v desktopové aplikaci Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Obsahuje kroky pro nastavení projektu pro sestavení pomocí sady Windows 10 SDK.|
|[Nasazení nativních aplikací klasické pracovní plochy](deploying-native-desktop-applications-visual-cpp.md)|Nasaďte nativní aplikace ve Windows.|

## <a name="related-articles"></a>Související články

|Název|Popis|
|-----------|-----------------|
|[C++ v sadě Visual Studio](../overview/visual-cpp-in-visual-studio.md)|Nadřazené téma pro obsah C++ pro Visual Developer|
[Vývoj pro .NET v C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Vytvořte obálky pro nativní C++ knihovny, které jim umožní komunikovat s aplikacemi a komponentami .NET.|
|[Přípony komponent pro .NET a UPW](../extensions/component-extensions-for-runtime-platforms.md)|Referenční informace pro elementy syntaxe, C++které sdílí C++/CX a/CLI.|
|[Univerzální aplikace pro Windows (C++)](../cppcx/universal-windows-apps-cpp.md)|Zapište aplikace UWP C++pomocí/CX nebo knihovny šablon prostředí Windows Runtime (WRL).|
|[Atributy C++ pro COM a .NET](attributes/cpp-attributes-com-net.md)|Nestandardní atributy pro programování pouze Windows pomocí .NET nebo COM.|
