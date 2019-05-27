---
title: C++ v sadě Visual Studio
description: Visual C++ je název pro kompilátor C++ společnosti Microsoft, editor kódu a související nástroje v integrovaném vývojovém prostředí sady Visual Studio. Použití jazyka Visual C++ pro vývoj aplikací pro Windows, Linux, Android a iOS.
ms.date: 05/14/2019
ms.technology: cpp-ide
helpviewer_keywords:
- Visual C++, home page
author: mikeblome
ms.author: mblome
ms.openlocfilehash: e9327f74f46590f4d4a71e56340dcadf6527fabb
ms.sourcegitcommit: bde3279f70432f819018df74923a8bb895636f81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174779"
---
# <a name="c-in-visual-studio"></a>C++ v sadě Visual Studio

> [!NOTE]
> Tuto dokumentaci pro vývojáře se vztahuje k sadě Visual Studio 2015 a novější. Pomocí selektoru verze v levém horním rohu stránky tak, aby odpovídaly vaší verze sady Visual Studio.
>
> Pokud hledáte balíček distribuovatelných součástí Visual C++ tak, aby mohly běžet programu, pokračujte [Microsoft Download Center](http://www.microsoft.com/download/) a zadejte **Visual C++** do vyhledávacího pole.

Microsoft Visual C++, obvykle zkrátila na Visual C++ nebo MSVC, je název pro C++, C a jazyk sestavení vývojářské nástroje a knihovny, které jsou k dispozici jako součást sady Visual Studio ve Windows. Tyto nástroje a knihovny umožňují vytvářet aplikace pro univerzální platformu Windows (UPW), nativních aplikací stolní počítače a servery Windows, multiplatformní knihovny a aplikace, které běží na Windows, Linux, Android a iOS, stejně jako spravovaných aplikací a knihoven, které používají rozhraní .NET Architektura. Visual C++ můžete použít k zápisu cokoli z jednoduché konzolové aplikace do nejvíce propracované a komplexní aplikace pro Windows desktop z ovladačů zařízení a součástí operačního systému pro mobilní zařízení a hry pro různé platformy z nejmenší zařízení IoT k více serverů vysokovýkonného výpočetního prostředí v cloudu Azure.

Visual Studio 2015 a 2017 2019 může být nainstalovaná vedle sebe. Visual Studio 2019 (v142 sada nástrojů kompilátoru) můžete použít k úpravám a vytváření aplikací pomocí sady nástrojů ze sady Visual Studio 2015 (v140) a Visual Studio 2017 (verze 141).

## <a name="whats-new-and-conformance-history"></a>Co je nového a historie shody

[Co je nového v C++ v sadě Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
Zjistěte, co je nového v sadě Visual Studio.

[Co je nového v jazyce C++ v aplikaci Visual Studio 2003 – 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md)<br/>
Zjistěte, co je nového v jazyce C++ pro každou verzi sady Visual Studio z 2003 – 2015.

[Vylepšení shody C++ se sadou Visual Studio](cpp-conformance-improvements.md)<br/>
Další informace o vylepšení shody C++ v sadě Visual Studio.

[Shoda jazyka Visual C++](visual-cpp-language-conformance.md)<br/>
Seznam stav shody funkcí v kompilátoru MSVC C++.

[Historie změn Visual C++ 2003–2015](../porting/visual-cpp-change-history-2003-2015.md)<br/>
Přečtěte si o nejnovějších změnách v předchozích verzích.

## <a name="install-visual-studio-and-upgrade-from-earlier-versions"></a>Instalace sady Visual Studio a upgradujete ze starší verze

[Instalace podpory jazyka C++ v sadě Visual Studio](../build/vscpp-step-0-installation.md)<br/>
Stáhněte si Visual Studio 2017 nebo Visual Studio 2019 a nainstalujte vizuál C++ sady nástrojů.

[Průvodce přenosem a upgradem Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)<br/>
Pokyny pro přenosy kódu a upgrade projektů na Visual Studio 2015 nebo novější využívat větší shoda s kompilátorem prostředí k C++ standardní a také dobu výrazně vylepšený kompilace a funkce zabezpečení, jako je zmírnění hrozby Spectre.

[Nástroje a funkce Visual C++ v různých edicích sady Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md)<br/>
Zjistěte informace o různých edicích sady Visual Studio.

[Podporované platformy](supported-platforms-visual-cpp.md)<br/>
Zjistěte, které platformy jsou podporovány.

## <a name="learn-c"></a>Informace o jazyku C++

[C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
Další informace o moderní C++ programovací techniky na základě v C ++ 11 a novějším, které umožňují napsat rychlé a bezpečné kód a vyhnout se mnoho nástrahy programování ve stylu C.

[Standardní C++](http://isocpp.org/)<br/>
Získejte informace o jazyce C++, přehled o moderním jazyce C++ a odkazy na knihy, články, rozhovory a události.

[Informace o jazyku Visual C++](../build/vscpp-step-1-create.md)<br/>
Začněte se učit jazyk C++.

[Visual C++ – ukázky](visual-cpp-samples.md)<br/>
Informace o ukázkách kódu.

## <a name="c-development-tools"></a>Vývojové nástroje C++

[Přehled o vývoji v jazyce C++ v sadě Visual Studio](overview-of-cpp-development.md)<br/>
Tom, jak pomocí integrovaného vývojového prostředí sady Visual Studio můžete vytvářet projekty, úpravy kódu, propojit s knihovnami, kompilace, ladění, vytvořit testy jednotek, provést statické analýzy, nasazení a další.

[Projekty a systémy sestavení](../build/projects-and-build-systems-cpp.md)<br/>
Jak vytvořit a nakonfigurovat možnosti kompilátoru a propojovacího programu MSVC projekty aplikace Visual Studio C++, projekty CMake a dalších typů projektů.

[Psaní a refaktoring kódu jazyka C++](../ide/writing-and-refactoring-code-cpp.md)<br/>
Jak používat si produktivitu funkcí v C++ editor Refaktorovat, navigaci, pochopit a psát kód.

[Ladění nativního kódu](/visualstudio/debugger/debugging-native-code)<br/>
Pomocí ladicího programu sady Visual Studio s projekty C++.

[Analýza kódu pro C/C++ – přehled](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)<br/>
Použití anotací SAL nebo podle dokumentu C++ Core Guidelines šachovnice provádět statické analýzy.

[Zápis testů jednotek pro C/C++ v sadě Visual Studio](/visualstudio/test/writing-unit-tests-for-c-cpp)<br/>
Vytvoření testování částí pomocí Microsoft Unit Testing Framework pro C++, Google Test, Boost.Test nebo CTest.

## <a name="write-applications-in-c"></a>Psaní aplikací v jazyce C++

[Aplikace pro Universal Windows](../windows/universal-windows-apps-cpp.md)<br/>
Vyhledejte si pokyny a referenční obsah ve středisku pro vývojáře v operačním systému Windows. Informace o vývoji aplikací pro UWP, naleznete v tématu [Úvod k univerzální platformě Windows](/windows/uwp/get-started/universal-application-platform-guide) a [vytvoření vaší první aplikace pro UWP pomocí jazyka C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

[Desktopové aplikace (C++)](../windows/desktop-applications-visual-cpp.md)<br/>
Zjistěte, jak vytvořit tradiční nativních desktopových aplikací C++ pro Windows.

[Programování pro .NET v jazyce C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
Zjistěte, jak vytvořit knihovny DLL, které umožňuje interoperabilitu mezi nativním jazyce C++ a .NET programy napsané v jazycích, jako je C# nebo Visual Basic.

[Programování v systému Linux](../linux/index.md)<br/>
Použijte Visual Studio IDE na kód a nasaďte na vzdáleném počítači s Linuxem pro kompilaci pomocí GCC.

[Vytvoření knihovny DLL jazyka C/C++ v sadě Visual Studio](../build/dlls-in-visual-cpp.md)<br/>
Zjistěte, jak používat Win32 a knihovny ATL a MFC pro vytvoření DLL knihoven pracovní plochy Windows a jak kompilovat a registrovat vytvořené knihovny DLL.

[Paralelní programování](../parallel/parallel-programming-in-visual-cpp.md)<br/>
Získejte další informace o použití knihovny PPL, C++ AMP, OpenMP a dalších funkcí, které se vztahují k multithreadingu v systému Windows.

[Osvědčené postupy zabezpečení](../security/security-best-practices-for-cpp.md)<br/>
Zjistěte, jak chránit aplikace před nebezpečným kódem a neoprávněným použitím.

[Cloudové a webové programování](../cloud/cloud-and-web-programming-in-visual-cpp.md)<br/>
V jazyce C++ máte několik možností pro připojení k webu a cloudu.

[Přístup k datům](../data/data-access-in-cpp.md)<br/>
Připojení k databázím pomocí rozhraní ODBC a OLE DB.

[Text a řetězce](../text/text-and-strings-in-visual-cpp.md)<br/>
Další informace o práci s jiným textovým a formáty řetězců a kódování pro místní i mezinárodní vývoje.

## <a name="languages-reference"></a>Odkaz na jazyky

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)

[C/C++ – referenční dokumentace preprocesoru](../preprocessor/c-cpp-preprocessor-reference.md)

[Referenční dokumentace jazyka C](../c-language/c-language-reference.md)

[Vnitřní funkce kompilátoru a jazyk sestavení](../intrinsics/compiler-intrinsics-and-assembly-language.md)

## <a name="c-libraries-in-visual-studio"></a>Knihovny C++ v sadě Visual Studio

Následující části obsahují informace o různých knihoven C a C++, které jsou zahrnuty v sadě Visual Studio.

[Referenční dokumentace knihovny CRT](../c-runtime-library/c-run-time-library-reference.md)<br/>
Obsahuje bezpečnější alternativy k funkcím, u kterých je známo, že představují bezpečnostní problém.

[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)<br/>
Standardní knihovně C++.

[Knihovna ATL (Active Template Library)](../atl/atl-com-desktop-components.md)<br/>
Podpora pro komponenty modelu COM a aplikace.

[Knihovny Microsoft Foundation třídy (MFC)](../mfc/mfc-desktop-applications.md)<br/>
Podpora pro vytváření aplikací klasické pracovní plochy, které mají tradiční uživatelské rozhraní nebo uživatelské rozhraní ve stylu Office.

[Knihovna PPL (Parallel Patterns Library)](../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Asynchronní a paralelní algoritmy, které jsou spouštěny na CPU.

[C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
Masivně paralelní algoritmy, které jsou spouštěny na GPU.

[Knihovna prostředí runtime Windows (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)<br/>
Univerzální aplikace pro platformu Windows (UPW) a komponenty.

[Programování pro .NET v jazyce C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
Programování pro modul Common Language Runtime (CLR).

## <a name="third-party-open-source-c-libraries"></a>Knihovny třetích stran opensourcového jazyka C++

Napříč platformami **vcpkg** nástroj příkazového řádku výrazně zjednodušuje zjišťování a instalaci více než 900 open source knihoven jazyka C++. See [vcpkg: Správce balíčků jazyka C++ pro Windows](../build/vcpkg.md).

## <a name="feedback-and-community"></a>Názory a komunita

[Postup nahlášení problému se sadou nástrojů Visual C++](how-to-report-a-problem-with-the-visual-cpp-toolset.md)<br/>
Naučíte se vytvářet zprávy o chybách efektivní proti sady nástrojů Visual C++ (kompilátoru, linkeru a dalších nástrojů) a způsoby, jak odeslat sestavy.

Microsoft [ C++ Blog týmu](https://devblogs.microsoft.com/cppblog/)<br/>
Další informace o nových funkcích a nejnovější informace od vývojářů C++ nástroje v sadě Visual Studio.

[Visual Studio Developer Community](https://developercommunity.visualstudio.com/)<br/>
Zjistěte, jak získat nápovědu, oznamovat chyby a posílat návrhy na vylepšení pro sadu Visual Studio.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C](../c-language/c-language-reference.md)
- [Referenční dokumentace knihovny CRT](../c-runtime-library/c-run-time-library-reference.md)
- [Vnitřní funkce kompilátoru a jazyk sestavení](../intrinsics/compiler-intrinsics-and-assembly-language.md)
