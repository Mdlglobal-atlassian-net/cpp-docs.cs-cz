---
title: Přehled programování v jazyce C++ v systému Windows | Microsoft Docs
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2096c36ec24c1ca7e20c789b8a1eb8c24589ccc1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="overview-of-windows-programming-in-c"></a>Přehled programování v C++ v systému Windows

Visual C++ můžete použít k zápisu různé druhy programy, které běží na počítači s Windows (x 86, x64 nebo ARM) v systému Windows server v cloudu nebo na Xbox. Kvalitně C++ – programy mít tyto vlastnosti:
- efektivní v požadavky na paměť
- ekonomické spotřeby energie 
- moci plně využít výhod vícejádrovými a mnoho základní zařízení
- vykonat obecné computing na grafický procesor (úloh GPGPU)   
- dokáže využívat jiné poslední zálohy v hardwaru.

Existuje několik široký kategorií aplikací pro Windows, které můžete vyvíjet pomocí Visual C++. Tyto kategorie mají různé programovací modely nebo modely aplikace, které byly zavedeny průběhu let. Každý model používá jiný knihovny a rozhraní API k poskytování přístupu k platformě a vytvoření uživatelského rozhraní, například windows a dialogová okna. Standardní knihovna C++, jakož i jiných výrobců knihovny můžete použít v některém z těchto kategorií, několik omezení pro UPW.

- [Univerzální aplikace Windows](#BK_WindowsUniversal). Třetí kategorii aplikací systému Windows byla zavedena v systému Windows 8 a podpora pro tuto kategorii aplikace pokračuje v systému Windows 10. Tyto aplikace jsou často označovány jako "Windows aplikací" a patří mezi ně desktop a mobile aplikací, které se zaměřují na široké škále zařízení. Můžete napsat tyto aplikace v jazyce C + +/ CX dialekt c++, která zahrnuje podporu pro vývoj pro prostředí Windows Runtime nebo ve standardní C++ v modelu COM pomocí knihovny Windows Runtime (WRL). Tyto aplikace byly původně navrženy pro spuštění celou obrazovku, i když v systému Windows 10 uživatelé mají možnost jejich spouštění v okně plochy. Tyto aplikace jsou dotykovým ovládáním, ale je snadno použitelné myši provoz preferujete uživatelé, nebo pokud není k dispozici dotykovou obrazovku. Tyto aplikace se distribuují z Microsoft Store, faktu, která vedla k nim volané aplikace "Úložiště".

Aplikace UWP je možné spouštět ve všech zařízeních Windows 10, jako jsou tablety a mobilní telefon, a také na ploše. Na ploše, budou moci spouštět jako plochy okno místo vždy spuštěn přes celou obrazovku. Tyto aplikace můžete také spouštět v zařízení Xbox a v budoucích zařízeních.  Aplikace UWP spustit v prostředí Windows Runtime, která poskytuje prvky uživatelského rozhraní, služeb a rozhraní pro různé hardwarová zařízení, které jsou podporovány v systému Windows.  

Můžete napsat aplikace UWP v jazyce C + +/ CX dialekt c++, můžete použít [C + +/ WinRT knihovna](https://moderncpp.com/)pro některé scénáře. Aplikace UWP kompilace nativního kódu a mít uživatelské rozhraní jazyka XAML nebo pomocí rozhraní DirectX. Prostředí Windows Runtime komponenty, které jsou zapsány v nativním kódu, můžete využívat UWP aplikací napsaných v dalších jazycích. Další informace najdete v tématu [vytvoření aplikace pro univerzální platformu Windows v jazyce C++](http://go.microsoft.com/fwlink/?LinkID=534976), [vytvoření vaší první UWP hry s použitím rozhraní DirectX](http://go.microsoft.com/fwlink/p/?LinkId=244656), a [vytváření prostředí Windows Runtime komponent v jazyce C++](http://go.microsoft.com/fwlink/p/?LinkId=244658).

   Tato kategorie zahrnuje také pomocí C++ pro základní komponenty a výpočetní kódu v rámci serveru a programování cloudu. Někdy kód náročných na výkon jádro serveru nebo cloudové aplikace je napsán v C++ pro zvýšení výkonu. Můžete takový kód kompilována knihovny DLL a použití z jazyka C# nebo Visual Basic.

- **Aplikace rozhraní .NET framework**. Většina aplikací rozhraní .NET Framework, které jsou napsané v C# nebo Visual Basic, ale můžete také C + +/ CLI (/ CLR – možnost kompilátoru v jazyce Visual C++). Doporučujeme používat C + +/ CLI pro vrstvu minimální spolupráce v větší aplikace, která zahrnuje spravovaná a nativní kód.

##  <a name="BK_WindowsUniversal"></a> Univerzální aplikace pro Windows

S Windows 10 aplikace je možné spouštět ve všech zařízeních Windows 10, jako jsou tablety a mobilní telefon, a také na ploše. Na ploše, budou moci spouštět jako plochy okno místo vždy spuštěn přes celou obrazovku. Tyto aplikace můžete také spouštět v zařízení Xbox a v budoucích zařízeních.  Programovací model pro oba typy aplikací se liší od aplikací klasické pracovní plochy Win32. Tyto aplikace systému Windows spustit v prostředí Windows Runtime, která obsahuje elementy uživatelského rozhraní, základní služby pro tyto aplikace a poskytuje, a rozhraní na různých hardwarová zařízení, které jsou podporovány. Tyto aplikace kompilace nativního kódu a mít uživatelské rozhraní jazyka XAML nebo pomocí rozhraní DirectX. Je také možné zapsat komponenty prostředí Windows Runtime v nativním kódu, který mohou využívat jiné aplikace pro Windows – patří mezi ně aplikace, které jsou napsané v C#, Visual Basic nebo JavaScript. Další informace najdete v tématu [vytvořit aplikaci UWP "Hello, world" v jazyce C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp), [vytvořit jednoduchou UWP hru s DirectX](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game), a [vytváření prostředí Windows Runtime komponent v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

> [!TIP]
> Pro Windows 10 můžete aplikaci převaděč plochy do balíčku plochy aplikace pro nasazení prostřednictvím Microsoft Store. Další informace najdete v tématu [pomocí modulu Runtime Visual C++ v projektu Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) a [přineste vaší aplikace na ploše do univerzální platformu Windows (UWP) s most plochy](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root).

Ukázky univerzální platformu Windows naleznete v části [Windows Universal ukázky z webu GitHub](https://github.com/Microsoft/Windows-universal-samples)

Pokud máte stávající projekt Windows 8.1 a chcete portu na Windows 10, najdete v části [přenos aplikací do univerzální platformy Windows](../porting/porting-to-the-universal-windows-platform-cpp.md). Pokud máte existující klasické ploše knihovny Win32 a kód, který chcete integrovat do aplikace pro UPW, najdete v části [postupy: použití existujícího kódu C++ v aplikaci pro univerzální platformu Windows](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md).

Další informace o UWP obecně platí, najdete v části [co je aplikace univerzální platformu Windows (UWP)?](/windows/uwp/get-started/whats-a-uwp).

Další informace o všech těchto pojmech najdete v tématu [Průvodce univerzálních aplikací pro Windows](http://go.microsoft.com/fwlink/p/?linkid=534605).

##  <a name="BK_Native"></a> Počítače a serverové aplikace

Základní informace o zápisu klienta aplikace systému Windows pro plochu naleznete v tématu [vývoj aplikací systému Windows v jazyce C++](http://msdn.microsoft.com/vstudio//hh304489) a [Úvod do Windows programování v C++](http://msdn.microsoft.com/library/windows/desktop/ff381398\(v=vs.85\).aspx).

Ve Windows 10 můžete vytvořit různé druhy desktopové programy Visual C++:

- Aplikace a nástroje příkazového řádku. Další informace najdete v tématu [konzolové aplikace](../windows/console-applications-in-visual-cpp.md).

- Zákaznické aplikace, které mají propracovanou podobu grafického uživatelského rozhraní. Další informace najdete v tématu [Hilo: vývoj aplikací C++ pro Windows](http://go.microsoft.com/fwlink/p/?LinkId=256417)

- Enterprise a obchodní aplikace, které běží na rozhraní .NET Framework. Většina aplikací rozhraní .NET Framework jsou napsané v C# nebo Visual Basic. Můžete použít C + +/ CLI k vytvoření spolupráce vrstvy, které umožňují kód .NET využívat nativní knihovny jazyka C++. Další informace najdete v tématu [.NET programování v jazyce C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

- Klienti SQL databáze, kteří běží v nativním kódu. Další informace najdete v tématu [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

- Doplňky aplikací sady Microsoft Office. Další informace najdete v tématu [vytváření Add-in C++ pro Outlook 2010](http://go.microsoft.com/fwlink/p/?LinkId=256420)

- Ovladače zařízení. Další informace najdete v tématu [ovladač Kit WDK (Windows)](http://go.microsoft.com/fwlink/p/?LinkId=256421)

- Služby systému Windows. Další informace najdete v tématu [Úvod do aplikace služby systému Windows](/dotnet/framework/windows-services/introduction-to-windows-service-applications).

Jazyk Visual C++ umožňuje zabalit téměř jakoukoli vlastní vysoce výkonnou funkcionalitu do Win32 DLL knihoven nebo do knihoven DLL modelu COM, které mohou být zpracovány C++ aplikacemi nebo aplikacemi, které byly napsány v jiných jazycích, například v jazyce C# nebo Visual Basic. Další informace o rozhraní DLLs WIn32 najdete v tématu [knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md). Další informace o COM vývoj najdete v tématu [modelu COM (Component Object)](https://msdn.microsoft.com/library/windows/desktop/ms680573).

## <a name="games"></a>hry

Rozhraní DirectX hry můžete spustit na počítači nebo Xbox. Další informace najdete v tématu [středisku pro vývojáře DirectX](http://go.microsoft.com/fwlink/p/?LinkId=256418).

## <a name="sdks-libraries-and-header-files"></a>Sady SDK, knihovny a soubory hlaviček

Visual C++ zahrnuje C Runtime Library (CRT), standardní knihovna C++ a další knihovny specifické pro společnost Microsoft. Zahrnout složky, které obsahují soubory hlaviček pro tyto knihovny se nachází buď v sadě Visual Studio Instalační adresář ve složce \VC\ nebo v případě CRT v instalační složce Nástroje sady Windows SDK.   

Můžete použít [Správce balíčků Vcpkg](../vcpkg.md) pohodlně nainstalovat stovky knihovny open-source třetích stran pro Windows.

Knihovny Microsoft patří:

- Třídy knihovny MFC (Microsoft Foundation Classes): Objektově orientovaný rámec pro vytváření tradičních programů operačního systému Windows (zejména podnikových aplikací), které mají bohatá uživatelská rozhraní obsahující tlačítka, seznamy, stromová zobrazení a další ovládací prvky. Další informace najdete v tématu [aplikace MFC plochy](../mfc/mfc-desktop-applications.md).

- Knihovna ATL (Active Template Library): Výkonné pomocné knihovny pro vytváření komponent modelu COM. Další informace najdete v tématu [ATL COM – součásti plochy](../atl/atl-com-desktop-components.md).

- Knihovna C++ AMP (C++ Accelerated Massive Parallelism): Knihovna, která umožňuje vysoce výkonné obecné výpočetní práce na GPU. Další informace najdete v tématu [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Modul Concurrency Runtime: Knihovna, která zjednodušuje práci paralelního a asynchronního programování pro vícejádrová a mnohojádrová zařízení. Další informace najdete v tématu [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

Mnoho programovacích scénářů pro Windows navíc také vyžaduje sadu Windows SDK obsahující soubory hlaviček, které umožňují přístup ke komponentám operačního systému Windows. Ve výchozím nastavení nainstaluje Visual Studio Windows SDK jako součást úlohy C++ plochy, umožňující vývoj univerzální aplikace pro Windows. Vývoj aplikací UWP, musíte na Windows 10 verzi sady Windows SDK. Informace najdete v tématu [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk). (Další informace o sady Windows SDK pro starší verze systému Windows najdete v tématu [Windows SDK archivu](https://developer.microsoft.com/windows/downloads/sdk-archive)). 

**Programové soubory (x86) \Windows sadách** je výchozím umístěním pro všechny verze sady Windows SDK, který jste nainstalovali.

Jiné platformy, jako je například konzola Xbox a Azure mají své vlastní sady SDK, které budete pravděpodobně muset nainstalovat. Další informace naleznete ve středisku pro vývojáře DirectX a ve středisku pro vývojáře Azure.

## <a name="development-tools"></a>Nástroje pro vývoj

Systém Visual Studio obsahuje výkonný ladicí program pro nativní kód, nástroje pro statickou analýzu, nástroje pro ladění grafiky, úplný editor kódu, podporu pro testování částí a mnoho dalších nástrojů a pomůcek. Další informace najdete v tématu [začít s vývojem pomocí sady Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio), a [IDE a nástrojů pro vývoj](../ide/ide-and-tools-for-visual-cpp-development.md).

## <a name="related-articles"></a>Související články

|Název|Popis|
|-----------|-----------------|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Nadřazené téma pro obsah vývojáře Visual C++.|
