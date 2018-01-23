---
title: "Visual C++ v sadě Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- unmanaged code, C++
- development environment, Visual C++
- unmanaged code
- Visual C++
- Visual C++, reference
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6fecc7f821bec90321095130fb21147d7227685c
ms.sourcegitcommit: 6f40bba1772a09ff0e3843d5f70b553e1a15ab50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2018
---
# <a name="visual-c-in-visual-studio"></a>Visual C++ v sadě Visual Studio

Visual Studio 2017 programovací jazyk a vývoj nástroje můžete vyvíjet nativní univerzální aplikace pro Windows, nativní počítače a serverové aplikace, knihovny a platformy, které spustit na Android a iOS, jakož i Windows a spravovat aplikace, které běží na rozhraní .NET Framework.

**Kdo je této dokumentace pro?**

Tento obsah je pro vývojáře C++, kteří jsou psaní programů.

- Pokud hledáte konkrétní distribuovatelného balíčku C++ a součásti režimu runtime tak, aby spuštění programu, přejděte k [Microsoft](http://www.microsoft.com/) web a zadejte **Visual C++ Redistributable** do vyhledávacího pole. Stáhněte a nainstalujte redistribuovatelného balíčku pro architekturu počítače (například x64 Pokud používáte systém Windows 64-bit) a verze aplikace Visual C++, které potřebujete. 

- Pokud hledáte Úvod do koncepty programování v C++, přejděte do jednoho z mnoha webů, které nabízejí tohoto obsahu nebo získat kopii [programování – principy a postup pomocí C++ (druhé vydání)](http://stroustrup.com/Programming/) podle inventor c++, Bjarnem Stroustrupem. Visual C++ obsahu předpokládá, že již máte základní znalost jazyka C++.

- Pokud hledáte Visual C++ compiler, budete muset stáhnout placené nebo bezplatná edice sady Visual Studio z [https://www.visualstudio.com/](https://www.visualstudio.com/).

## <a name="general-information-about-visual-c"></a>Obecné informace o aplikaci Visual C++

[Co je nového pro Visual C++](what-s-new-for-visual-cpp-in-visual-studio.md)  
Zjistěte, co je nového v jazyce Visual C++.

[Vylepšení shody C++ se sadou Visual Studio 2017](cpp-conformance-improvements-2017.md)  
Další informace o vylepšení shoda C++ ve Visual Studio 2017.

[Přizpůsobení jazyka Visual C++](visual-cpp-language-conformance.md)  
Seznam shoda stav funkce v jazyce Visual C++.

[Historie změn Visual C++ 2003–2015](porting/visual-cpp-change-history-2003-2015.md)  
Další informace o nejnovějších změn v předchozích verzích.

[C++ vás vítá zpět](cpp/welcome-back-to-cpp-modern-cpp.md)  
Další informace o moderní verze jazyka C++ programování techniky na základě C ++ 11 a C ++ 14, které vám umožní zápisu rychlé a bezpečné kódu a vyhnout se řadu nástrahy stylu jazyka C programování.

[Postup nahlášení problému se sadou nástrojů Visual C++](how-to-report-a-problem-with-the-visual-cpp-toolset.md)  
 Naučte se vytvořit efektivní chybách vůči nástrojů Visual C++ (kompilátoru, linkeru a další nástroje) a způsoby, jak odeslat sestavy.

[Průvodce přenosem a upgradem Visual C++](porting/visual-cpp-porting-and-upgrading-guide.md)  
Pokyny pro kód – portování a upgrade projektů na Visual C++ v aplikaci Visual Studio 2017, včetně portování kódu C++ do Windows 10 a univerzální platformu Windows.

[Blog týmu Visual C++](http://blogs.msdn.com/b/vcblog/)  
 Další informace o nových funkcích a o nejnovější informace z vývojáři [!INCLUDE[vcprvc](build/includes/vcprvc_md.md)].

[Stažení sady Visual Studio](http://go.microsoft.com/fwlink/p/?linkid=235233)  
Stáhněte si Visual C++.

[Nástroje a funkce Visual C++ v různých edicích sady Visual Studio](ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)  
Zjistěte informace o různých edicích sady Visual Studio.

[Podporované platformy](supported-platforms-visual-cpp.md)  
Zjistěte, které platformy jsou podporovány.

[Visual C++ – ukázky](visual-cpp-samples.md)  
Informace o ukázkách kódu.

[Komunity vývojářů v sadě Visual Studio](https://developercommunity.visualstudio.com/)  
Zjistěte, jak získat nápovědu, oznamovat chyby a posílat návrhy na vylepšení pro sadu Visual Studio.

## <a name="writing-applications-in-c"></a>Psaní aplikací v jazyce C++

[Univerzální aplikace pro Windows](windows/universal-windows-apps-cpp.md)  
Vyhledejte si pokyny a referenční obsah ve středisku pro vývojáře v operačním systému Windows. Informace o vývoji aplikací pro Windows Store najdete v tématu [aplikace pro vývoj Windows Store pomocí sady Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=248364) a [aplikace plán pro Windows Store pomocí C++](http://go.microsoft.com/fwlink/p/?LinkId=244654).

[Desktopové aplikace (Visual C++)](windows/desktop-applications-visual-cpp.md)  
Získejte informace o vytváření aplikací klasické pracovní plochy, které mají smyčky zpráv a zpětná volání.

[Knihovny DLL v jazyce Visual C++](build/dlls-in-visual-cpp.md)  
Zjistěte, jak používat Win32 a knihovny ATL a MFC pro vytvoření DLL knihoven pracovní plochy Windows a jak kompilovat a registrovat vytvořené knihovny DLL.

[Paralelní programování](parallel/parallel-programming-in-visual-cpp.md)  
Získejte další informace o použití knihovny PPL, C++ AMP, OpenMP a dalších funkcí, které se vztahují k multithreadingu v systému Windows.

[Osvědčené postupy zabezpečení](security/security-best-practices-for-cpp.md)  
Zjistěte, jak chránit aplikace před nebezpečným kódem a neoprávněným použitím.

[Cloudové a webové programování](cloud/cloud-and-web-programming-in-visual-cpp.md)  
V jazyce C++ máte několik možností pro připojení k webu a cloudem.

[Přístup k datům](http://msdn.microsoft.com/Library/a9455752-39c4-4457-b14e-197772d3df0b)  
Připojování k databázím pomocí rozhraní ODBC a další technologie pro přístup k databázi.

[Text a řetězce](text/text-and-strings-in-visual-cpp.md)  
Informace o práci s jiným textovým a formáty řetězců a kódování pro místní i mezinárodní vývoj.

## <a name="c-development-tools"></a>Nástroje pro vývoj C++

Chcete-li zjistit, o tom, jak vytváření projektů, pracovat s soubory zdrojového kódu, propojit knihovny, kompilovat, ladění, profilu, nasazení a další, přečtěte si téma [IDE a nástrojů pro vývoj](ide/ide-and-tools-for-visual-cpp-development.md).

## <a name="c-language-reference"></a>Referenční příručka jazyka C++

Informace o jazyka C++ najdete v tématu [referenční příručka jazyka C++](cpp/cpp-language-reference.md).

Informace o C++ preprocessor najdete v tématu [referenční dokumentace jazyka C/C++ Preprocessor](preprocessor/c-cpp-preprocessor-reference.md).

## <a name="c-libraries-in-visual-studio"></a>Knihovny jazyka C++ v sadě Visual Studio

Následující části obsahují informace o různých knihovny jazyka C++, které jsou součástí Visual C++.

[Referenční dokumentace knihovny CRT](c-runtime-library/c-run-time-library-reference.md)  
Obsahuje bezpečnější alternativy k funkcím, u kterých je známo, že představují bezpečnostní problém.

[Standardní knihovna C++](standard-library/cpp-standard-library-reference.md)  
Standardní knihovně C++.

[Knihovna ATL (Active Template Library)](atl/atl-com-desktop-components.md)  
Podpora pro aplikace a komponenty modelu COM.

[Knihovny Microsoft Foundation Class (MFC)](mfc/mfc-desktop-applications.md)  
Podpora pro vytváření aplikací klasické pracovní plochy, které mají tradiční uživatelské rozhraní nebo uživatelské rozhraní ve stylu Office.

[Knihovna PPL (Parallel Patterns Library)](parallel/concrt/parallel-patterns-library-ppl.md)  
Asynchronní a paralelní algoritmy, které jsou spouštěny na CPU.

[C++ AMP (C++ Accelerated Massive Parallelism)](parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)  
Masivně paralelní algoritmy, které jsou spouštěny na GPU.

[Knihovna Windows šablon Runtime (WRL)](http://msdn.microsoft.com/library/windows/apps/hh438466.aspx)  
[!INCLUDE[win8_appname_long](build/includes/win8_appname_long_md.md)]aplikace a součásti.

[Programování pro .NET v jazyce C++/CLI (Visual C++)](dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)  
Programování pro modul Common Language Runtime (CLR).

Viz také v dokumentaci k [STL/CLR](dotnet/stl-clr-library-reference.md) a [knihovna podpory C++](dotnet/cpp-support-library.md).

## <a name="other-c-libraries"></a>Další knihovny jazyka C++

Tato část obsahuje odkazy na knihovny, které nejsou součástí sady Visual Studio, ale je možné stáhnout a použít s Visual C++.

[Zvýšení výkonu](http://www.boost.org/)  
Oblíbené a často používané knihovny.

[C++ REST SDK](http://casablanca.codeplex.com).  
Knihovna Microsoft pro komunikaci s webovými službami přes protokol HTTP.

## <a name="more-resources"></a>Další prostředky

[Prostředky Visual C++](http://msdn.microsoft.com/vstudio/hh386302.aspx)  
Další materiály k jazyku Visual C++

[Standardní C++](http://isocpp.org/)  
Získejte informace o jazyce C++, přehled o moderním jazyce C++ a odkazy na knihy, články, rozhovory a události.

[Learn Visual C++](http://msdn.microsoft.com/vstudio/hh386302.aspx)  
Začněte se učit jazyk C++.

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka C](c-language/c-language-reference.md)   
[Referenční dokumentace běhové knihovny jazyka C](c-runtime-library/c-run-time-library-reference.md)   
[Vnitřní funkce kompilátoru a jazyk sestavení](intrinsics/compiler-intrinsics-and-assembly-language.md)
