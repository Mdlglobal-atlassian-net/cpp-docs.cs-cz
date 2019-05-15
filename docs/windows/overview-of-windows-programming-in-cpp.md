---
title: Přehled programování v C++ v systému Windows
ms.date: 05/06/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: f2cdb0d0225b47391ee18c398b7789ab42ca8f40
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65708211"
---
# <a name="overview-of-windows-programming-in-c"></a>Přehled programování v C++ v systému Windows

Existuje několik kategorií aplikací Windows, které můžete vytvořit pomocí jazyka C++. Každý má své vlastní programovací model a sadu knihovny specifické pro Windows, ale standardní knihovny C++, stejně jako knihovny třetích stran C++ lze použít v některé z nich. 

## <a name="command-line-console-applications"></a>Aplikace příkazového řádku (konzola)

Aplikace konzoly C++ spusťte z příkazového řádku v okně konzoly a může zobrazit jenom textový výstup. Další informace najdete v tématu [konzolové aplikace](console-applications-in-visual-cpp.md).
 
## <a name="native-desktop-client-applications"></a>Nativní klientská aplikace

Termín *nativní klientská aplikace* odkazuje na C nebo C++ oddílové aplikaci, která používá původní nativní [rozhraní API Windows C a/nebo rozhraní API modelu COM](/windows/desktop/apiindex/windows-api-list) pro přístup k operačním systémem. Tato rozhraní API představují samy o sobě převážně v C. Při vytváření tohoto typu aplikace, máte taky možnost výběru programovat přímo s smyčku zpráv ve stylu jazyka C, který zpracovává události v operačním systému, nebo s použitím *Microsoft Foundation Classes* (MFC), knihovnu C++, která obaluje Win32 způsobem, který je o něco objektově orientovaný. Žádný přístup se považuje za "moderní" ve srovnání s univerzální platformu Windows (viz níže), ale oba jsou stále plně podporované a mít miliony řádků kódu spuštěného v celém světě ještě dnes. Aplikace Win32, na kterém běží v okně vyžaduje pro vývojáře pro práci s zpráv Windows uvnitř procedury funkce Windows explicitně. Bez ohledu na název můžete jako (x86) 32bitové nebo 64bitové (x64) binární zkompilovat aplikaci Win32. V sadě Visual Studio IDE je shodný podmínky x86 a Win32.

Abyste mohli začít s programováním tradiční Windows C++, naleznete v tématu [Win32 a C++ vám začít](/windows/desktop/LearnWin32/learn-to-program-for-windows). Po získání některé znalost Win32 ji bude snazší naučit [desktopových aplikací knihovny MFC](../mfc/mfc-desktop-applications.md). Příklad tradiční desktopové aplikace C++, využívající sofistikované grafiky, naleznete v tématu [Hilo: Vývoj aplikací pro Windows v jazyce C++](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx).

### <a name="c-or-net"></a>.NET nebo C++? 

Pro scénáře nejvíce desktopové aplikace (jinými slovy, UPW ne cílení), zvažte použití C# k vytvoření uživatelského rozhraní. Je to proto, že je obecně méně složitý, méně náchylný programování rozhraní .NET a má Modernější objektově orientované rozhraní API než Win32 nebo MFC. Ve většině případů je více než odpovídající jeho výkon. Windows Presentation Foundation (WPF) pro bohaté grafické funkce rozhraní .NET, a může využívat Win32, jakož i moderní Windows rozhraní API modulu Runtime (viz níže UPW). Obecně platí doporučujeme pomocí jazyka C++ pro desktopové aplikace, když budete potřebovat:

- mít naprostou kontrolu nad využití paměti
- co nejvíce ekonomiku spotřeby energie
- využití GPU pro obecné účely
- přístup k rozhraní DirectX
- Silná použití standardních knihovnách jazyka C++

Můžete vytvořit uživatelské rozhraní v C# a používat C++vyhodnocovací, aby aplikace využívat nativní C++ knihovny. Další informace najdete v tématu [programování v rozhraní .NET s C++vyhodnocovací](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="com-components"></a>Komponenty modelu COM

[Modelu COM (Component Object)](/windows/desktop/com/the-component-object-model) je specifikace, které umožňuje programy napsané v různých jazycích, aby mezi sebou komunikovat. Řada Windows komponenty jsou implementovány jako objekty modelu COM a pravidlům standardní modelu COM pro vytváření objektů rozhraní zničení objektu a zjišťování.  Použití objektů COM v aplikacích klasické pracovní plochy jazyka C++ je poměrně přímočarý, ale zápis objektu modelu COM je složitější. [Aktivní šablony knihovny (ATL)](../atl/atl-com-desktop-components.md) poskytuje makra a pomocných funkcí, které zjednodušují vývoj COM. Další informace najdete v tématu [desktopové komponenty ATL COM](../atl/atl-com-desktop-components.md).

## <a name="windows-universal-apps"></a>Univerzální aplikace pro Windows

Univerzální platforma Windows (UPW) je moderní rozhraní Windows API. U aplikací pro UPW běží na všech zařízeních Windows 10, použijte uživatelské rozhraní XAML a jsou plně dotykově ovládaný. Další informace o UPW, naleznete v tématu [co je aplikace pro univerzální platformu Windows (UPW)?](/windows/uwp/get-started/whats-a-uwp) a [Průvodce univerzálních aplikací pro Windows](/windows/uwp/get-started/universal-application-platform-guide).

Původní C++ podpora UWP se skládal z (1) C++/CX dialekt C++ pomocí syntaxe přípony nebo (2) Windows Runtime knihovny (WRL) která je založena na standardu C++ a modelu COM. Obě C++/CX a WRL jsou stále podporovány. Pro nové projekty doporučujeme [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) zcela která je založena na standardu C++ a poskytuje rychlejší výkon. 

## <a name="desktop-bridge"></a>Přemostění na Desktop

Ve Windows 10 můžete zabalit existující aplikace klasické pracovní plochy nebo objekt modelu COM jako aplikace pro UPW a přidat UPW funkce, jako je touch nebo volání rozhraní API ze sady moderní rozhraní Windows API. Můžete také přidat aplikace pro UPW pro desktop řešení v sadě Visual Studio a balíček je společně v jednom balíčku a používat rozhraní Windows API pro komunikaci mezi nimi.

V sadě Visual Studio 2017 verze 15.4 nebo novější můžete vytvořit projekt Windows Application balíček výrazně zjednodušit práci při balení aplikace klasické pracovní plochy. S ohledem na jaké registru volá platí několik omezení nebo používá rozhraní API pro aplikace klasické pracovní plochy, ale v mnoha případech můžete vytvořit kód alternativní cesty dosáhnout podobné funkce jako při spuštění v balíčku aplikace. Další informace najdete v tématu [přemostění na Desktop](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Hry

Hry rozhraní DirectX můžete spustit na PC nebo konzolách Xbox. Další informace najdete v tématu [grafika DirectX a hraní her](/windows/desktop/directx).

## <a name="sql-server-database-clients"></a>Klienti databáze systému SQL Server

Pro přístup k databázím serveru SQL Server z nativního kódu, použijte rozhraní ODBC nebo Oledb. Další informace najdete v tématu [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Ovladače zařízení Windows

Ovladače jsou nízké úrovně komponenty, které zpřístupňují data z hardwarových zařízení k aplikacím a další součásti operačního systému. Další informace najdete v tématu [Windows Driver Kit (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>služby systému Windows

Windows *služby* je program, který může běžet na pozadí bez zásahu uživatele nebo vůbec žádné. V systému UNIX se nazývají *procesy démon*. Další informace najdete v tématu [služby](/windows/desktop/services/services).

## <a name="sdks-libraries-and-header-files"></a>Sady SDK, knihovny a soubory hlaviček

Visual Studio obsahuje knihovny Runtime jazyka C (CRT), standardní knihovny C++ a další knihovny specifické pro společnost Microsoft. Zahrnout složky obsahující soubory hlaviček těchto knihoven jsou umístěny v adresáři instalace sady Visual Studio ve složce \VC\ nebo v případě CRT v instalační složce Nástroje sady Windows SDK.

Můžete použít [Správce balíčků Vcpkg](../build/vcpkg.md) stovky open source knihoven třetích stran jednoduše instalace pro Windows.

Knihovny Microsoft patří:

- Microsoft Foundation Classes (MFC): Objektově orientovaný rámec pro vytváření tradičních programů Windows – zejména podnikových aplikací, které mají bohatá uživatelská rozhraní obsahující tlačítka, seznamy, stromová zobrazení a další ovládací prvky. Další informace najdete v tématu [desktopových aplikací knihovny MFC](../mfc/mfc-desktop-applications.md).

- Knihovna aktivní šablony (knihovny ATL): Výkonné pomocné knihovny pro vytváření komponent COM. Další informace najdete v tématu [desktopové komponenty ATL COM](../atl/atl-com-desktop-components.md).

- C++ AMP (C++ Accelerated Massive Parallelism): Knihovna, která umožňuje vysoce výkonné obecné výpočetní práce na GPU. Další informace najdete v tématu [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Modul Concurrency Runtime: Knihovna, která zjednodušuje práci paralelního a asynchronního programování pro Vícejádrová a mnohojádrová zařízení. Další informace najdete v tématu [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

Mnoho programovacích scénářů pro Windows navíc také vyžaduje sadu Windows SDK obsahující soubory hlaviček, které umožňují přístup ke komponentám operačního systému Windows. Ve výchozím nastavení nainstaluje Visual Studio jako součást sady funkcí C++ Desktop, umožňující vývoj aplikací pro Windows Universal Windows SDK. K vývoji aplikací pro UWP, musíte verzi sady Windows SDK pro Windows 10. Informace najdete v tématu [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk). (Další informace o sady Windows SDK u starších verzí systému Windows, najdete v článku [sady Windows SDK archivu](https://developer.microsoft.com/windows/downloads/sdk-archive)).

**Program soubory (x86) \Windows Kits** je výchozím umístěním pro všechny verze sady Windows SDK, kterou jste nainstalovali.

Jiné platformy, jako je například konzola Xbox a Azure mají své vlastní sady SDK, které budete pravděpodobně muset nainstalovat. Další informace naleznete ve středisku pro vývojáře DirectX a ve středisku pro vývojáře Azure.

## <a name="development-tools"></a>Nástroje pro vývoj

Systém Visual Studio obsahuje výkonný ladicí program pro nativní kód, nástroje pro statickou analýzu, nástroje pro ladění grafiky, úplný editor kódu, podporu pro testování částí a mnoho dalších nástrojů a pomůcek. Další informace najdete v tématu [začít s vývojem pomocí sady Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio), a [C++ přehled vývoje v sadě Visual Studio](../overview/overview-of-cpp-development.md).

## <a name="in-this-section"></a>V tomto oddílu
|Název|Popis|
|-----------|-----------------|
|[Návod: Vytvoření programu ve standardním C++](walkthrough-creating-a-standard-cpp-program-cpp.md)| Vytvořte konzolovou aplikaci Windows.|
|[Návod: Vytváření desktopových aplikací Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Vytvoření jednoduché aplikace klasické pracovní plochy Windows.|
|[Desktopový průvodce pro Windows](windows-desktop-wizard.md)|Chcete-li vytvořit nové projekty Windows pomocí průvodce.|
|[Knihovna ATL (Active Template Library)](../atl/TOC.md)|Použití knihovny ATL vytváření komponent modelu COM v jazyce C++.|
|[Knihovna MFC (Microsoft Foundation Classes)](../mfc/TOC.md)|Použití knihovny MFC k vytvoření velké nebo malé aplikací Windows pomocí dialogových oken a ovládacích prvků|
|[Sdílené třídy knihoven ATL a MFC](../atl-mfc-shared/TOC.md)|Pomocí třídy například CString, které jsou sdíleny v ATL a MFC.|
|[Přístup k datům](../data/data-access-in-cpp.md)| OLE DB a rozhraní ODBC|
|[Text a řetězce](../text/text-and-strings-in-visual-cpp.md)|Různými typy řetězců na Windows.|
|[Prostředky pro vytvoření hry s použitím rozhraní DirectX](resources-for-creating-a-game-using-directx.md)
|[Postupy: Použití sady Windows 10 SDK v desktopové aplikaci Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows SDK|
|[Práce se zdrojovými soubory](working-with-resource-files.md)|Jak přidat obrázky, ikony, tabulek řetězců a dalších prostředků pro aplikace klasické pracovní plochy.|
|[Prostředky pro vytvoření hry s použitím rozhraní DirectX (C++)](resources-for-creating-a-game-using-directx.md)|Obsahuje odkazy na obsah pro vytváření her v C++.|
|[Postupy: Použití sady Windows 10 SDK v desktopové aplikaci Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Obsahuje kroky pro vytvoření projektu pro sestavení pomocí Windows 10 SDK.|
|[Nasazení nativních aplikací klasické pracovní plochy](deploying-native-desktop-applications-visual-cpp.md)|Nasazení nativních aplikací pro Windows.|


## <a name="related-articles"></a>Související články

|Název|Popis|
|-----------|-----------------|
|[C++ v sadě Visual Studio](../overview/visual-cpp-in-visual-studio.md)|Nadřazené téma pro obsah pro vývojáře v jazyce Visual C++.|
[Vývoj pro .NET v C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Vytváření obálek pro nativní knihovny C++, které umožňují komunikaci s aplikacemi .NET a součásti.|
|[Přípony komponent pro .NET a UPW](../extensions/component-extensions-for-runtime-platforms.md)|Referenční informace pro prvky syntaxe sdílí C++/CX a C++vyhodnocovací.|
|[Univerzální aplikace pro Windows (C++)](universal-windows-apps-cpp.md)|Psaní aplikací UPW pomocí C++/CX nebo Windows Runtime šablony knihovny (WRL).|
|[Atributy C++ pro COM a .NET](attributes/cpp-attributes-com-net.md)|Nestandardní atributy Windows – pouze pro programování pomocí rozhraní .NET nebo modelu COM.|

