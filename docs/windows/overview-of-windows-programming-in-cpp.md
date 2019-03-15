---
title: Přehled programování v C++ v systému Windows
ms.date: 11/15/2018
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 6338b390b11c58f3ebac2af1bb568ea3c3470cd1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810442"
---
# <a name="overview-of-windows-programming-in-c"></a>Přehled programování v C++ v systému Windows

Existuje několik kategorií aplikací Windows, které můžete vytvořit pomocí jazyka C++. Každý má své vlastní programovací model a sadu knihovny specifické pro Windows, ale standardní knihovny C++, stejně jako knihovny třetích stran C++ lze použít v některé z nich. 

## <a name="command-line-console-applications"></a>Aplikace příkazového řádku (konzola)

Aplikace konzoly C++ spusťte z příkazového řádku v okně konzoly a může zobrazit jenom textový výstup. Další informace najdete v tématu [konzolové aplikace](console-applications-in-visual-cpp.md).
 
## <a name="native-desktop-client-applications"></a>Nativní klientská aplikace

Termín *nativní klientská aplikace* odkazuje na C nebo C++ oddílové aplikaci, která používá původní rozhraní Win32 API Windows pro přístup k operačním systémem. Tato rozhraní API představují samy o sobě převážně v C. Při vytváření tohoto typu aplikace, máte taky možnost výběru programovat přímo s smyčku zpráv ve stylu jazyka C, který zpracovává události v operačním systému, nebo s použitím *Microsoft Foundation Classes* (MFC), knihovnu C++, která obaluje Win32 způsobem, který je o něco objektově orientovaný. Žádný přístup se považuje za "moderní" ve srovnání s univerzální platformu Windows (viz níže), ale oba jsou stále plně podporované a mít miliony řádků kódu spuštěného v celém světě ještě dnes.

Abyste mohli začít s programováním tradiční Windows C++, naleznete v tématu [Win32 a C++ vám začít](/windows/desktop/LearnWin32/learn-to-program-for-windows). Po získání některé znalost Win32 ji bude snazší naučit [desktopových aplikací knihovny MFC](/mfc/mfc-desktop-applications). Příklad tradiční desktopové aplikace C++, využívající sofistikované grafiky, naleznete v tématu [Hilo: Vývoj aplikací pro Windows v jazyce C++](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx).

### <a name="c-or-net"></a>.NET nebo C++? 

Pro scénáře nejvíce desktopové aplikace (jinými slovy, UPW ne cílení), zvažte použití C# a .NET. Je to proto, že je obecně méně složitý, méně náchylný programování rozhraní .NET a má Modernější objektově orientované rozhraní API než Win32 nebo MFC. Ve většině případů je více než odpovídající jeho výkon. Windows Presentation Foundation (WPF) pro bohaté grafické funkce rozhraní .NET, a může využívat Win32, jakož i moderní Windows rozhraní API modulu Runtime (viz níže UPW). Obecně platí doporučujeme pomocí jazyka C++ pro desktopové aplikace, když budete potřebovat:

- mít naprostou kontrolu nad využití paměti
- co nejvíce ekonomiku spotřeby energie
- využití GPU pro obecné účely
- přístup k rozhraní DirectX
- Silná použití standardních knihovnách jazyka C++

## <a name="com-components"></a>Komponenty modelu COM

Mnoho částí operačního systému Windows jsou založeny na modelu COM (Component Object) definující binární standard, která umožňuje komponentě využívat z klientské aplikace napsané v libovolném jazyce počítače. V jazyce C++ můžete aktivní šablony knihovny (ATL) zjednodušují vytváření komponenty modelu COM. Další informace najdete v tématu [modelu COM (Component Object)](/windows/desktop/com/component-object-model--com--portal) a [desktopové komponenty ATL COM](../atl/atl-com-desktop-components.md).

## <a name="windows-universal-apps"></a>Univerzální aplikace pro Windows

Univerzální platforma Windows (UPW) je moderní rozhraní Windows API. U aplikací pro UPW běží na všech zařízeních Windows 10, použijte uživatelské rozhraní XAML a jsou plně dotykově ovládaný. Další informace o UPW, naleznete v tématu [co je aplikace pro univerzální platformu Windows (UPW)?](/windows/uwp/get-started/whats-a-uwp) a [Průvodce univerzálních aplikací pro Windows](/windows/uwp/get-started/universal-application-platform-guide).

Původní podpora C++ pro UPW se skládal z (1) C + +/ CX, dialekt jazyka C++ s rozšíření syntaxe nebo (2) Windows Runtime knihovny (WRL) která je založena na standardní C++ a modelu COM. Jazyce C + +/ CX a WRL jsou stále podporovány. Pro nové projekty doporučujeme [C + +/ WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) který je zcela založená na standard C++ a poskytuje vyšší výkon. 

Pro Windows 10, můžete zabalit existující aplikace klasické pracovní plochy jazyka C++ jako-je pro nasazení přes Microsoft Store. Další informace najdete v tématu [balíček aplikací klasické pracovní plochy (přemostění na Desktop)](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Hry

Hry rozhraní DirectX můžete spustit na PC nebo konzolách Xbox. Další informace najdete v tématu [grafika DirectX a hraní her](/windows/desktop/directx).

## <a name="net-wrappers-for-c-libraries"></a>.NET obálky pro knihovny C++

Můžete použít C + +/ CLI k vytvoření spolupráce vrstvy, která umožňuje kódu .NET do nativních knihoven jazyka C++. Další informace najdete v tématu [.NET programování v jazyce C + +/ CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="sql-server-database-clients"></a>Klienti databáze systému SQL Server

Pro přístup k databázím serveru SQL Server z nativního kódu, použijte rozhraní ODBC nebo Oledb. Další informace najdete v tématu [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Ovladače zařízení Windows

Ovladače jsou nízké úrovně komponenty, které zpřístupňují data z hardwarových zařízení k aplikacím a další součásti operačního systému. Další informace najdete v tématu [Windows Driver Kit (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>služby systému Windows

Windows *služby* je program, který může běžet na pozadí bez zásahu uživatele nebo vůbec žádné. V systému UNIX se nazývají *procesy démon*. Další informace najdete v tématu [služby](/windows/desktop/services/services).

## <a name="sdks-libraries-and-header-files"></a>Sady SDK, knihovny a soubory hlaviček

Visual Studio obsahuje knihovny Runtime jazyka C (CRT), standardní knihovny C++ a další knihovny specifické pro společnost Microsoft. Zahrnout složky obsahující soubory hlaviček těchto knihoven jsou umístěny v adresáři instalace sady Visual Studio ve složce \VC\ nebo v případě CRT v instalační složce Nástroje sady Windows SDK.

Můžete použít [Správce balíčků Vcpkg](../vcpkg.md) stovky open source knihoven třetích stran jednoduše instalace pro Windows.

Knihovny Microsoft patří:

- Microsoft Foundation Classes (MFC): Objektově orientovaný rámec pro vytváření tradičních programů Windows – zejména podnikových aplikací, které mají bohatá uživatelská rozhraní obsahující tlačítka, seznamy, stromová zobrazení a další ovládací prvky. Další informace najdete v tématu [desktopových aplikací knihovny MFC](../mfc/mfc-desktop-applications.md).

- Knihovna aktivní šablony (knihovny ATL): Výkonné pomocné knihovny pro vytváření komponent COM. Další informace najdete v tématu [desktopové komponenty ATL COM](../atl/atl-com-desktop-components.md).

- C++ AMP (C++ Accelerated Massive Parallelism): Knihovna, která umožňuje vysoce výkonné obecné výpočetní práce na GPU. Další informace najdete v tématu [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Modul Concurrency Runtime: Knihovna, která zjednodušuje práci paralelního a asynchronního programování pro Vícejádrová a mnohojádrová zařízení. Další informace najdete v tématu [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

Mnoho programovacích scénářů pro Windows navíc také vyžaduje sadu Windows SDK obsahující soubory hlaviček, které umožňují přístup ke komponentám operačního systému Windows. Ve výchozím nastavení nainstaluje Visual Studio jako součást sady funkcí C++ Desktop, umožňující vývoj aplikací pro Windows Universal Windows SDK. K vývoji aplikací pro UWP, musíte verzi sady Windows SDK pro Windows 10. Informace najdete v tématu [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk). (Další informace o sady Windows SDK u starších verzí systému Windows, najdete v článku [sady Windows SDK archivu](https://developer.microsoft.com/windows/downloads/sdk-archive)).

**Program soubory (x86) \Windows Kits** je výchozím umístěním pro všechny verze sady Windows SDK, kterou jste nainstalovali.

Jiné platformy, jako je například konzola Xbox a Azure mají své vlastní sady SDK, které budete pravděpodobně muset nainstalovat. Další informace naleznete ve středisku pro vývojáře DirectX a ve středisku pro vývojáře Azure.

## <a name="development-tools"></a>Nástroje pro vývoj

Systém Visual Studio obsahuje výkonný ladicí program pro nativní kód, nástroje pro statickou analýzu, nástroje pro ladění grafiky, úplný editor kódu, podporu pro testování částí a mnoho dalších nástrojů a pomůcek. Další informace najdete v tématu [začít s vývojem pomocí sady Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio), a [C++ přehled vývoje v sadě Visual Studio](../overview-of-cpp-development.md).

## <a name="in-this-section"></a>V tomto oddílu
|Název|Popis|
|-----------|-----------------|
|[Desktopové aplikace pro Windows v C++](desktop-applications-visual-cpp.md)| Postup vytvoření tradiční desktopové aplikace.|
|[Knihovna ATL (Active Template Library)](../atl/TOC.md)|Použití knihovny ATL vytváření komponent modelu COM v jazyce C++.|
|[Knihovna MFC (Microsoft Foundation Classes)](../mfc/TOC.md)|Použití knihovny MFC k vytvoření velké nebo malé aplikací Windows pomocí dialogových oken a ovládacích prvků|
|[Sdílené třídy knihoven ATL a MFC](../atl-mfc-shared/TOC.md)|Pomocí třídy například CString, které jsou sdíleny v ATL a MFC.|
|[Vývoj pro .NET v C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Vytváření obálek pro nativní knihovny C++, které umožňují komunikaci s aplikacemi .NET a součásti.|
|[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)|Referenční informace pro prvky syntaxe sdílí C + +/ CX a C + +/ CLI.|
|[Univerzální aplikace pro Windows (C++)](universal-windows-apps-cpp.md)|Psaní aplikací UPW pomocí C + +/ CX nebo Windows Runtime šablony knihovny (WRL).|
|[Atributy C++ pro COM a .NET](attributes/cpp-attributes-com-net.md)|Nestandardní atributy Windows – pouze pro programování pomocí rozhraní .NET nebo modelu COM.|

## <a name="related-articles"></a>Související články

|Název|Popis|
|-----------|-----------------|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Nadřazené téma pro obsah pro vývojáře v jazyce Visual C++.|
