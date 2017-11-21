---
title: "Přehled programování v jazyce C++ v systému Windows | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 30a5138c4ec95b2d57f56b5cc4b5731c1be073ad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="overview-of-windows-programming-in-c"></a>Přehled programování v C++ v systému Windows
Jazyk Visual C++ lze použít pro vytvoření širokého spektra programů, které lze spustit na počítačích s operačním systémem Windows (x86, x64 nebo ARM), serveru Windows, v cloudu nebo na konzole Xbox. Kvalitně napsané C++ programy jsou rychlé, efektivní, ekonomické ve spotřebě energie a schopné plně využít výhod vícejádrových nebo mnohojádrových zařízení, běžných výpočtů na grafických kartách (GPGPU) a dalších nově vzniklých hardwarových řešeních.  
  
 Existuje několik široký kategorií aplikací pro Windows, které můžete vyvíjet pomocí Visual C++. Tyto kategorie mají různé programovací modely nebo modely aplikace, což znamená, že používají různé knihovny a rozhraní API, které poskytují přístup na platformu a zadejte uživatelské rozhraní.  
  
-   [Univerzální aplikace Windows](#BK_WindowsUniversal). Třetí kategorii aplikací systému Windows byla zavedena v systému Windows 8 a podpora pro tuto kategorii aplikace pokračuje v systému Windows 10. Tyto aplikace jsou často označovány jako "Windows aplikací" a patří mezi ně desktop a mobile aplikací, které se zaměřují na široké škále zařízení. Můžete napsat tyto aplikace v jazyce C + +/ CX dialekt c++, která zahrnuje podporu pro vývoj pro prostředí Windows Runtime nebo ve standardní C++ v modelu COM pomocí knihovny Windows Runtime (WRL). Tyto aplikace byly původně navrženy pro spuštění celou obrazovku, i když v systému Windows 10 uživatelé mají možnost jejich spouštění v okně plochy. Tyto aplikace jsou dotykovým ovládáním, ale je snadno použitelné myši provoz preferujete uživatelé, nebo pokud není k dispozici dotykovou obrazovku. Tyto aplikace jsou distribuované z Windows Store, faktu, která vedla k nim volané "Aplikace pro Windows Store."  
  
-   [Plocha, Server a cloudové aplikace a hry](#BK_Native). Tato kategorie zahrnuje aplikace Windows Desktop, někdy označuje jako aplikace Win32, protože tyto aplikace byly pomocí rozhraní API Win32 na před Windows 8, všechny aplikace systému Windows byly v této kategorii. Aplikace v této kategorii můžete použít pro uživatelské rozhraní MFC a knihovna ATL pro interakci s součásti systému Windows, které jsou obvykle COM – objekty.  
  
     Aplikace, komponenty nebo knihovny napsané pomocí standardní C++ také nevejde se do této kategorie patří.  
  
     Tato kategorie zahrnuje také pomocí C++ pro základní komponenty a výpočetní kódu v rámci serveru a programování cloudu. Někdy kód náročných na výkon jádro serveru nebo cloudové aplikace je napsán v C++ pro zvýšení výkonu. Můžete takový kód kompilována knihovny DLL a použití z jazyka C# nebo Visual Basic.  
  
-   **Aplikace rozhraní .NET framework**. Většina aplikací rozhraní .NET Framework, které jsou napsané v C# nebo Visual Basic, ale můžete také C + +/ CLI (/ CLR – možnost kompilátoru v jazyce Visual C++). Doporučujeme používat C + +/ CLI pro vrstvu minimální spolupráce v větší aplikace, která zahrnuje spravovaná a nativní kód.  
  
##  <a name="BK_WindowsUniversal"></a>Univerzální aplikace pro Windows  
 S Windows 10 aplikace je možné spouštět ve všech zařízeních Windows 10, jako jsou tablety a mobilní telefon, a také na ploše. Na ploše, budou moci spouštět jako plochy okno místo vždy spuštěn přes celou obrazovku. Tyto aplikace můžete také spouštět v zařízení Xbox a v budoucích zařízeních.  Programovací model pro oba typy aplikací se liší od aplikací klasické pracovní plochy Win32. Tyto aplikace systému Windows spustit v prostředí Windows Runtime, která obsahuje elementy uživatelského rozhraní, základní služby pro tyto aplikace a poskytuje, a rozhraní na různých hardwarová zařízení, které jsou podporovány. Tyto aplikace kompilace nativního kódu a mít uživatelské rozhraní jazyka XAML nebo pomocí rozhraní DirectX. Je také možné zapsat komponenty prostředí Windows Runtime v nativním kódu, který mohou využívat jiné aplikace pro Windows – patří mezi ně aplikace, které jsou napsané v C#, Visual Basic nebo JavaScript. Další informace najdete v tématu [vytvoření první aplikace Windows Store pomocí C++](http://go.microsoft.com/fwlink/?LinkID=534976), [vytvoření vaší první Windows Store hry s použitím rozhraní DirectX](http://go.microsoft.com/fwlink/p/?LinkId=244656), a [vytváření prostředí Windows Runtime komponent v jazyce C++](http://go.microsoft.com/fwlink/p/?LinkId=244658).  

 > [!TIP]  
> Pro Windows 10 můžete aplikaci převaděč plochy do balíčku plochy aplikace pro nasazení prostřednictvím portálu Windows Store. Další informace najdete v tématu [pomocí modulu Runtime Visual C++ v projektu Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) a [přineste vaší aplikace na ploše do univerzální platformu Windows (UWP) s most plochy](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root).
  
  
 Ukázky univerzální platformu Windows naleznete v části [Windows Universal ukázky z webu GitHub](https://github.com/Microsoft/Windows-universal-samples)  
  
 Pokud máte stávající projekt Windows 8.1 a chcete portu na Windows 10, najdete v části [přenos aplikací do univerzální platformy Windows](../porting/porting-to-the-universal-windows-platform-cpp.md). Pokud máte existující klasické ploše knihovny Win32 a kód, který chcete integrovat do aplikace pro UPW, najdete v části [postupy: použití existujícího kódu C++ v aplikaci pro univerzální platformu Windows](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md).  
  
 Můžete také psát aplikace, hry a součásti Universal Windows bez použití C + +/ CX; Místo toho můžete knihovna šablon C++ Windows Runtime (knihovna šablon C++ Runtime Windows). Další informace najdete v tématu [Windows Runtime C++ šablony knihovny (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).  
  
 S [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], můžete vyvíjet univerzální aplikace pro Windows 10 desktop a mobilní zařízení se systémem Windows. Můžete také vývoj aplikací pro Windows 8.1 a Windows Phone 8.1 aplikace v [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], ale to pokud chcete udělat, musíte nejdřív nainstalovat Visual Studio 2013 ve stejném počítači a pak nakonfigurujte projektu pro použití **Visual Studio 2013 (v120)** sada nástrojů . Chcete-li nakonfigurovat toto nastavení ve vašem projektu, otevřete vlastnosti projektu a v **Obecné** nastavte **sada nástrojů platformy** k **Visual Studio 2013 (v120)**.  
  
 Pokud nainstalujete nástroje Phone 8.0 v instalačním programu sady Visual Studio, můžete také vybrat Windows Phone 8.0.  
  
 Nová koncepce zavedená v systému Windows 10 volat rozhraní API kontrakty nahradí původní praxi cílení na konkrétní verze Windows. Místo toho můžete které rozhraní API smlouvy aplikace potřebám a pak spustí na jakémkoli zařízení systému Windows, který podporuje tyto smlouvy. Kontrakt rozhraní API je sada stabilní rozhraní API, které poskytují přístup k prostředkům platformu nebo zařízení. Kontrakty rozhraní API může být v systému projektu zahrnuty jako odkazy. V projektu sady Visual Studio Pokud přidáte odkaz na konkrétní sadu SDK rozšíření, pak Visual Studio přidá odpovídající kontrakty rozhraní API.  
  
 Další informace o všech těchto pojmech najdete v tématu [Průvodce univerzálních aplikací pro Windows](http://go.microsoft.com/fwlink/?LinkId=534605).  
  
##  <a name="BK_Native"></a>Plocha, Server a cloudové aplikace a hry  
 V cloudu můžete napsat sestavení Azure nativního kódu v jazyce C++ a volání do nich z webové role, které jsou vytvořené v C#. Další informace najdete v tématu [Azure SDK](http://go.microsoft.com/fwlink/p/?LinkId=256416).  
  
 Základní informace o zápisu klienta aplikace systému Windows pro plochu naleznete v tématu [vývoj aplikací systému Windows v jazyce C++](http://msdn.microsoft.com/vstudio//hh304489) a [Úvod do Windows programování v C++](http://msdn.microsoft.com/library/windows/desktop/ff381398\(v=vs.85\).aspx).  
  
 Ve Windows 10 můžete vytvořit různé druhy programy Visual C++:  
  
-   Aplikace a nástroje příkazového řádku. Další informace najdete v tématu [konzolové aplikace](../windows/console-applications-in-visual-cpp.md).  
  
-   Hry rozhraní DirectX, které lze spustit na PC nebo konzolách Xbox. Další informace najdete v tématu [středisku pro vývojáře DirectX](http://go.microsoft.com/fwlink/p/?LinkId=256418).  
  
-   Zákaznické aplikace, které mají propracovanou podobu grafického uživatelského rozhraní. Další informace najdete v tématu [Hilo: vývoj aplikací C++ pro Windows](http://go.microsoft.com/fwlink/p/?LinkId=256417)  
  
-   Enterprise a byznys aplikace, které používají rámec .NET Framework, nebo slouží jako most mezi aplikacemi rámce .NET Framework a aplikacemi a komponentami, které byly napsány v nativním kódu. Další informace najdete v tématu [.NET programování v jazyce C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).  
  
-   Klienti SQL databáze, kteří běží v nativním kódu. Další informace najdete v tématu [SQL Server Native Client](http://go.microsoft.com/fwlink/p/?LinkId=256419).  
  
-   Doplňky aplikací sady Microsoft Office. Další informace najdete v tématu [vytváření Add-in C++ pro Outlook 2010](http://go.microsoft.com/fwlink/p/?LinkId=256420)  
  
-   Ovladače zařízení. Další informace najdete v tématu [ovladač Kit WDK (Windows)](http://go.microsoft.com/fwlink/p/?LinkId=256421)  
  
-   Služby systému Windows. Další informace najdete v tématu [Úvod do aplikace služby systému Windows](/dotnet/framework/windows-services/introduction-to-windows-service-applications).  
  
 Jazyk Visual C++ umožňuje zabalit téměř jakoukoli vlastní vysoce výkonnou funkcionalitu do Win32 DLL knihoven nebo do knihoven DLL modelu COM, které mohou být zpracovány C++ aplikacemi nebo aplikacemi, které byly napsány v jiných jazycích, například v jazyce C# nebo Visual Basic. Další informace o rozhraní DLLs WIn32 najdete v tématu [knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md). Další informace o COM vývoj najdete v tématu [modelu COM (Component Object)](http://msdn.microsoft.com/en-us/375d29a7-a1f3-4bd8-8621-bad7a049b2aa).  
  
## <a name="sdks-and-header-files"></a>SDK a soubory hlaviček  
 Visual C++ zahrnuje C Runtime Library (CRT), standardní knihovna C++ a další knihovny specifické pro společnost Microsoft. Zahrnout složky, které obsahují soubory hlaviček pro tyto knihovny jsou že buď nachází v instalačním adresáři sady Visual Studio ve složce \VC\ nebo v případě CRT, instalační složky sady Windows SDK, například Windows Kits\10 v souborech programu Složka pro Windows 10 SDK.  Knihovny Microsoft patří:  
  
-   Třídy knihovny MFC (Microsoft Foundation Classes): Objektově orientovaný rámec pro vytváření tradičních programů operačního systému Windows (zejména podnikových aplikací), které mají bohatá uživatelská rozhraní obsahující tlačítka, seznamy, stromová zobrazení a další ovládací prvky. Další informace najdete v tématu [aplikace MFC plochy](../mfc/mfc-desktop-applications.md).  
  
-   Knihovna ATL (Active Template Library): Výkonné pomocné knihovny pro vytváření komponent modelu COM. Další informace najdete v tématu [ATL COM – součásti plochy](../atl/atl-com-desktop-components.md).  
  
-   Knihovna C++ AMP (C++ Accelerated Massive Parallelism): Knihovna, která umožňuje vysoce výkonné obecné výpočetní práce na GPU. Další informace najdete v tématu [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).  
  
-   Modul Concurrency Runtime: Knihovna, která zjednodušuje práci paralelního a asynchronního programování pro vícejádrová a mnohojádrová zařízení. Další informace najdete v tématu [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).  
  
 Mnoho programovacích scénářů pro Windows navíc také vyžaduje sadu Windows SDK obsahující soubory hlaviček, které umožňují přístup ke komponentám operačního systému Windows. Ve výchozím nastavení nainstalujte všechny edice sady Visual Studio 2015 SDK Windows, která umožňuje vývoj univerzální aplikace pro Windows. K vývoji univerzální aplikace pro Windows pro Windows 10, musíte na Windows 10 verzi sady Windows SDK. Informace o sadě Windows 10 SDK najdete v tématu [Windows 10 SDK](http://go.microsoft.com/fwlink/p/?LinkId=534603). (Další informace o sady Windows SDK pro starší verze systému Windows najdete v tématu [Přehled sady Windows SDK](http://msdn.microsoft.com/Library/9a2db508-5b77-43f8-afa4-1ca82d24bb83)).  
  
 Jiné platformy, jako je například konzola Xbox a Azure mají své vlastní sady SDK, které budete pravděpodobně muset nainstalovat. Další informace naleznete ve středisku pro vývojáře DirectX a ve středisku pro vývojáře Azure.  
  
## <a name="development-tools"></a>Nástroje pro vývoj  
 Systém Visual Studio obsahuje výkonný ladicí program pro nativní kód, nástroje pro statickou analýzu, nástroje pro ladění grafiky, úplný editor kódu, podporu pro testování částí a mnoho dalších nástrojů a pomůcek. Další informace najdete v tématu [vývoj aplikací v sadě Visual Studio](http://msdn.microsoft.com/en-us/97490c1b-a247-41fb-8f2c-bc4c201eff68), a [IDE a nástrojů pro vývoj](../ide/ide-and-tools-for-visual-cpp-development.md).  
  
## <a name="related-articles"></a>Související články  
  
|Název|Popis|  
|-----------|-----------------|  
|[Visual C++](../visual-cpp-in-visual-studio.md)|Nadřazené téma pro obsah vývojáře Visual C++.|