---
title: Přehled programování v C++ v systému Windows
ms.date: 09/17/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 8ab7fbf7c955b1c828ef583aa639eda7409cf167
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359943"
---
# <a name="overview-of-windows-programming-in-c"></a>Přehled programování v C++ v systému Windows

Existuje několik širokých kategorií aplikací systému Windows, které můžete vytvořit pomocí jazyka C++. Každý z nich má svůj vlastní programovací model a sadu knihoven specifických pro Windows, ale standardní knihovny Jazyka C++ a knihovny Jazyka C++ třetích stran lze použít v libovolné z nich.

Tato část popisuje, jak používat visual studio a knihovny obálky knihovny Knihovny MFC/ATL k vytvoření programů systému Windows. Dokumentaci na samotné platformě Windows naleznete v [dokumentaci k systému Windows](/windows/index).

## <a name="command-line-console-applications"></a>Aplikace příkazového řádku (konzoly)

Aplikace konzoly C++ běží z příkazového řádku v okně konzoly a mohou zobrazovat pouze textový výstup. Další informace naleznete [v tématu Vytvoření projektu konzolové aplikace jazyka C++](../get-started/tutorial-console-cpp.md).

## <a name="native-desktop-client-applications"></a>Nativní klientské aplikace pro stolní počítače

Nativní *desktopová klientská aplikace* je aplikace s okny jazyka C nebo C++, která pro přístup k operačnímu systému používá původní nativní api [jazyka Windows C nebo COM (COM).](/windows/win32/apiindex/windows-api-list) Tato api jsou sama zapsána převážně v C. Existuje více než jeden způsob, jak vytvořit nativní desktopové aplikace: Můžete programovat pomocí Win32 API přímo, pomocí smyčky zpráv ve stylu C, který zpracovává události operačního systému. Nebo můžete programovat pomocí *Microsoft Foundation Classes* (MFC), lehce objektově orientované knihovny C++, která zabalí Win32. Ani jeden přístup je považován za "moderní" ve srovnání s univerzální platformou Windows (UPW), ale oba jsou stále plně podporovány a mají miliony řádků kódu běžící v dnešním světě. Aplikace Win32, která běží v okně vyžaduje, aby vývojář pracovat explicitně se zprávami systému Windows uvnitř funkce procedury systému Windows. Navzdory názvu aplikace Win32 lze zkompilovat jako 32bitový (x86) nebo 64bitový (x64) binární. V ide sady Visual Studio jsou synonyma termíny x86 a Win32.

Pokud chcete začít s tradičním programováním ve Windows C++, přečtěte si informace [o tématu Začínáme s Win32 a C++](/windows/win32/LearnWin32/learn-to-program-for-windows). Poté, co získáte nějaké znalosti win32, bude snazší se dozvědět o [mfc desktopové aplikace](../mfc/mfc-desktop-applications.md). Příklad tradiční desktopové aplikace jazyka C++, který používá sofistikovanou grafiku, najdete v [tématu Hilo: Vývoj aplikací jazyka C++ pro Windows](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx).

### <a name="c-or-net"></a>C++ nebo .NET?

Obecně platí. Ve většině případů je jeho výkon více než přiměřený. Rozhraní .NET je vybaveno windows presentation foundation (WPF) pro bohatou grafiku a můžete využívat win32 i moderní rozhraní API prostředí Windows Runtime. Obecně platí, že doporučujeme používat c++ pro desktopové aplikace, pokud potřebujete:

- přesná kontrola nad využitím paměti
- maximální hospodárnost spotřeby energie
- využití GPU pro obecné výpočty
- přístup k rozhraní DirectX
- vysoké využití standardních knihoven C++

Je také možné kombinovat výkon a účinnost jazyka C++ s programováním .NET. Můžete vytvořit uživatelské rozhraní v jazyce C# a pomocí jazyka C++/CLI povolit aplikaci využívat nativní knihovny C++. Další informace naleznete [v tématu .NET Programování s C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="com-components"></a>Komponenty modelu COM

[Model COM (COM)](/windows/win32/com/the-component-object-model) je specifikace, která umožňuje programům napsaným v různých jazycích vzájemně komunikovat. Mnoho součástí systému Windows je implementováno jako objekty modelu COM a dodržuje standardní pravidla modelu COM pro vytváření objektů, zjišťování rozhraní a zničení objektu.  Použití objektů COM z aplikací klasické pracovní plochy jazyka C++ je poměrně jednoduché, ale psaní vlastního objektu COM je pokročilejší. Knihovna [active template Library (ATL)](../atl/atl-com-desktop-components.md) poskytuje makra a pomocné funkce, které zjednodušují vývoj com. Další informace naleznete v tématu [ATL COM desktop components](../atl/atl-com-desktop-components.md).

## <a name="universal-windows-platform-apps"></a>Univerzální aplikace platformy Windows

Univerzální platforma Windows (UPW) je moderní rozhraní API systému Windows. Aplikace UPW běží na libovolném zařízení s Windows 10, používají XAML pro uživatelské rozhraní a jsou plně dotykové. Další informace o programu UPW najdete v [tématech Co je univerzální aplikace pro platformu Windows (UPW)](/windows/uwp/get-started/whats-a-uwp) a [Průvodce univerzálními aplikacemi windows](/windows/uwp/get-started/universal-application-platform-guide).

Původní podpora jazyka C++ pro UPW se skládala z (1) C++/CX, dialektu jazyka C++ s rozšířeními syntaxe nebo (2) knihovny Runtime (WRL) systému Windows, která je založena na standardních jazycích C++ a COM. C++/CX i WRL jsou stále podporovány. Pro nové projekty doporučujeme [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), který je zcela založen na standardní mj.

## <a name="desktop-bridge"></a>Most plochy

Ve Windows 10 můžete zabalit existující desktopovou aplikaci nebo objekt COM jako aplikaci UPW a přidat funkce UPW, jako je dotykové ovládání, nebo volat rozhraní API z moderní sady rozhraní API systému Windows. Můžete také přidat aplikaci UPW do řešení plochy v sadě Visual Studio a zabalit je do jednoho balíčku a použít windows api komunikovat mezi nimi.

Visual Studio 2017 verze 15.4 a novější umožňuje vytvořit projekt balíčku aplikací pro Windows, který výrazně zjednoduší práci s balením stávající desktopové aplikace. Několik omezení platí pro volání registru nebo api, která může vaše desktopová aplikace používat. V mnoha případech však můžete vytvořit alternativní cesty kódu k dosažení podobné funkce při spuštění v balíčku aplikace. Další informace naleznete [v tématu Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Hry

Hry DirectX lze spouštět na počítači nebo xboxu. Další informace naleznete v [tématu DirectX Graphics and Gaming](/windows/win32/directx).

## <a name="sql-server-database-clients"></a>Databázoví klienti serveru SQL Server

Chcete-li získat přístup k databázím serveru SQL Server z nativního kódu, použijte rozhraní ODBC nebo OLE DB. Další informace naleznete v tématu [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Ovladače zařízení systému Windows

Ovladače jsou součásti nižší úrovně, které zpřístupní data z hardwarových zařízení aplikacím a dalším součástem operačního systému. Další informace naleznete v [tématu Windows Driver Kit (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>Služby pro Windows

*Služba* systému Windows je program, který lze spustit na pozadí s malou nebo žádnou interakcí uživatele. Tyto programy se nazývají *daemons* na systémech UNIX. Další informace naleznete v [tématu Services](/windows/win32/services/services).

## <a name="sdks-libraries-and-header-files"></a>Sady SDK, knihovny a soubory hlaviček

Visual Studio obsahuje knihovnu Runtime C (CRT), standardní knihovnu Jazyka C++ a další knihovny specifické pro Microsoft. Většina složek, které obsahují soubory hlaviček pro tyto knihovny, je umístěna v instalačním adresáři sady Visual Studio ve složce \VC\. Soubory hlaviček systému Windows a CRT se nacházejí v instalační složce sady Windows SDK.

[Správce balíčků Vcpkg](../build/vcpkg.md) umožňuje pohodlně nainstalovat stovky open-source knihoven třetích stran pro Windows.

Knihovny Společnosti Microsoft zahrnují:

- Třídy knihovny MFC (Microsoft Foundation Classes): Objektově orientovaný rámec pro vytváření tradičních programů operačního systému Windows (zejména podnikových aplikací), které mají bohatá uživatelská rozhraní obsahující tlačítka, seznamy, stromová zobrazení a další ovládací prvky. Další informace naleznete v [tématu MFC Desktop Applications](../mfc/mfc-desktop-applications.md).

- Knihovna ATL (Active Template Library): Výkonné pomocné knihovny pro vytváření komponent modelu COM. Další informace naleznete v tématu [ATL COM Desktop Components](../atl/atl-com-desktop-components.md).

- Knihovna C++ AMP (C++ Accelerated Massive Parallelism): Knihovna, která umožňuje vysoce výkonné obecné výpočetní práce na GPU. Další informace naleznete [v tématu C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Modul Concurrency Runtime: Knihovna, která zjednodušuje práci paralelního a asynchronního programování pro vícejádrová a mnohojádrová zařízení. Další informace naleznete v [tématu Souběžnost Runtime](../parallel/concrt/concurrency-runtime.md).

Mnoho programovacích scénářů pro Windows navíc také vyžaduje sadu Windows SDK obsahující soubory hlaviček, které umožňují přístup ke komponentám operačního systému Windows. Ve výchozím nastavení sada Visual Studio nainstaluje sadu Windows SDK jako součást úlohy plochy jazyka C++, které umožňuje vývoj univerzálních aplikací pro Windows. K vývoji aplikací UPW potřebujete verzi sady Windows SDK pro Windows 10. Další informace naleznete v [tématu Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk). (Další informace o sadách Windows SDK pro starší verze systému Windows naleznete v [archivu sady Windows SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)).

**Program Files (x86)\Windows Kit je** výchozí umístění pro všechny verze sady Windows SDK, které jste nainstalovali.

Jiné platformy, jako je například konzola Xbox a Azure mají své vlastní sady SDK, které budete pravděpodobně muset nainstalovat. Další informace naleznete ve středisku pro vývojáře DirectX a ve středisku pro vývojáře Azure.

## <a name="development-tools"></a>Nástroje pro vývoj

Systém Visual Studio obsahuje výkonný ladicí program pro nativní kód, nástroje pro statickou analýzu, nástroje pro ladění grafiky, úplný editor kódu, podporu pro testování částí a mnoho dalších nástrojů a pomůcek. Další informace naleznete [v tématu Začínáme s vývojem s Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio)a Přehled vývoje jazyka [C++ v sadě Visual Studio](../overview/overview-of-cpp-development.md).

## <a name="in-this-section"></a>V tomto oddílu

|Nadpis|Popis|
|-----------|-----------------|
|[Návod: Vytvoření standardního programu c++](walkthrough-creating-a-standard-cpp-program-cpp.md)| Vytvořte aplikaci konzoly systému Windows.|
|[Návod: Vytváření desktopových aplikací Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Vytvořte nativní desktopovou aplikaci windows.|
|[Desktopový průvodce pro Windows](windows-desktop-wizard.md)|Průvodce slouží k vytváření nových projektů systému Windows.|
|[Knihovna ATL (Active Template Library)](../atl/atl-com-desktop-components.md)|Pomocí knihovny KNIHOVNY KNIHOVNY ATL můžete vytvářet komponenty modelu COM v jazyce C++.|
|[Knihovna MFC (Microsoft Foundation Classes)](../mfc/mfc-desktop-applications.md)|Použití knihovny MFC k vytváření velkých nebo malých aplikací systému Windows s dialogovými okny a ovládacími prvky|
|[Sdílené třídy knihoven ATL a MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)|Použijte třídy, jako je CString, které jsou sdíleny v knihovně ATL a Knihovna mfc.|
|[Přístup k datům](../data/data-access-in-cpp.md)| TECHNOLOGIE OLE DB a ROZHRANÍ ODBC|
|[Text a řetězce](../text/text-and-strings-in-visual-cpp.md)|Různé typy řetězců v systému Windows.|
|[Prostředky pro vytvoření hry s použitím rozhraní DirectX](resources-for-creating-a-game-using-directx.md)
|[Postupy: Použití sady Windows 10 SDK v desktopové aplikaci Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Sada SDK pro Windows|
|[Práce se zdrojovými soubory](working-with-resource-files.md)|Jak přidat obrázky, ikony, tabulky řetězců a další prostředky do aplikace na ploše.|
|[Zdroje informací pro vytvoření hry pomocí rozhraní DirectX (C++)](resources-for-creating-a-game-using-directx.md)|Odkazy na obsah pro vytváření her v jazyce C++.|
|[Postupy: Použití sady Windows 10 SDK v desktopové aplikaci Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Obsahuje kroky pro nastavení projektu k sestavení pomocí sady Windows 10 SDK.|
|[Nasazení nativních aplikací klasické pracovní plochy](deploying-native-desktop-applications-visual-cpp.md)|Nasazujte nativní aplikace v systému Windows.|

## <a name="related-articles"></a>Související články

|Nadpis|Popis|
|-----------|-----------------|
|[C++ v sadě Visual Studio](../overview/visual-cpp-in-visual-studio.md)|Nadřazené téma pro obsah vývojáře visual c++.|
[Vývoj pro .NET v C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Vytvořte obálky pro nativní knihovny jazyka C++, které umožňují komunikaci s aplikacemi a součástmi rozhraní .NET.|
|[Přípony komponent pro .NET a UPW](../extensions/component-extensions-for-runtime-platforms.md)|Odkaz na prvky syntaxe sdílené c++/CX a C++/CLI.|
|[Univerzální aplikace pro Windows (C++)](../cppcx/universal-windows-apps-cpp.md)|Psát aplikace UPW pomocí C++/CX nebo Windows Runtime Template Library (WRL).|
|[Atributy C++ pro COM a .NET](attributes/cpp-attributes-com-net.md)|Nestandardní atributy pro programování pouze pro systém Windows pomocí rozhraní .NET nebo COM.|
