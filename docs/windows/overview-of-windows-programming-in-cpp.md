---
title: Přehled Windows programování v jazyce C++ | Dokumentace Microsoftu
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
ms.openlocfilehash: 59c0a9701c1714e1d96829a28144c921e5c00e11
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206714"
---
# <a name="overview-of-windows-programming-in-c"></a>Přehled programování v C++ v systému Windows

Visual C++ můžete použít k zápisu mnoha typů programů, které běží na počítači s Windows (x 86, x64 nebo ARM) na Windows serveru v cloudu nebo na Xboxu. Kvalitně napsané programy v jazyce C++ mají tyto vlastnosti:
- efektivní v požadavky na paměť
- ekonomické ve spotřebě energie 
- možnost využívat všech výhod Vícejádrová a mnohojádrová zařízení
- možné obecné výpočetní na grafický procesor (úloh GPGPU)  
- moct využít výhod dalších mnohojádrových hardwaru.

Existuje několik kategorií aplikací Windows, které vyvíjíte v jazyce Visual C++. Tyto kategorie mají různé programovací modely nebo modely aplikace, které byly zavedeny v průběhu let. Každý model používá různé knihovny a rozhraní API poskytnout přístup na platformu a vytváření uživatelských rozhraní, jako je například windows a dialogových oknech. Standardní knihovny C++, stejně jako knihovny třetích stran je možné v některém z těchto kategorií s několika omezeními pro UPW.

- [Univerzální aplikace pro Windows](#BK_WindowsUniversal). Třetí kategorie aplikací pro Windows byla zavedena v systému Windows 8 a podpora pro tuto kategorii aplikace pokračuje ve Windows 10. Tyto aplikace jsou často označovány jako "Windows apps" a zahrnují desktopových a mobilních aplikací, které se zaměřují různých zařízeních. Tyto aplikace můžete psát v jazyce C + +/ CX, dialekt jazyka C++, která zahrnuje podporu pro vývoj pro Windows Runtime nebo ve standardním jazyce C++ s modelu COM s využitím knihovna Windows Runtime (WRL). Tyto aplikace byly původně navržen pro spouštění na celé obrazovce a i když ve Windows 10 mají uživatelé možnost spuštění v okně klasické pracovní plochy. Tyto aplikace jsou dotykových, ale je snadno použitelné myši provoz, pokud uživatelé dávají přednost určování nebo pokud není k dispozici dotykovou obrazovku. Tyto aplikace jsou distribuované z Microsoft Store, což vedlo k je volána "Store" aplikace.

U aplikací pro UPW je možné spouštět na všech zařízeních Windows 10, jako jsou tablety a mobilní telefony, stejně jako v klientských počítačích. Na ploše, je možné spouštět jako okno klasické pracovní plochy, ne vždy spuštěný celou obrazovku. Tyto aplikace můžete spustit také na Xboxu a v budoucích zařízení.  Aplikace UWP běží na Windows Runtime, která poskytuje prvky uživatelského rozhraní, služby a rozhraní pro různé hardwarová zařízení, které jsou podporované ve Windows.

Aplikace UWP můžete psát v jazyce C + +/ CX, dialekt jazyka C++, můžete použít [C + +/ knihoven WinRT](https://moderncpp.com/)pro několik scénářů. U aplikací pro UPW kompilovány do nativního kódu a mají XAML uživatelské rozhraní nebo pomocí rozhraní DirectX. Součásti prostředí Windows Runtime, které jsou napsány v nativním kódu, můžete využívat aplikace UPW napsané v jiných jazycích. Další informace najdete v tématu [vytvoření aplikace pro univerzální platformu Windows v jazyce C++](http://go.microsoft.com/fwlink/?LinkID=534976), [vytvořit svoji první hru UPW pomocí DirectX](http://go.microsoft.com/fwlink/p/?LinkId=244656), a [součástí vytváření prostředí Windows Runtime v jazyce C++](http://go.microsoft.com/fwlink/p/?LinkId=244658).

   Tato kategorie zahrnuje také pomocí jazyka C++ pro součásti jádra a výpočetní kód v rámci serveru a programování v cloudu. Někdy náročné na výkon kódu v jádru serveru nebo cloudové aplikace je napsaný v jazyce C++ se pro zajištění maximálního výkonu. Můžete kompilovat takového kódu do knihovny DLL a použití z jazyka C# nebo Visual Basic.

- **Aplikace rozhraní .NET framework**. Většina aplikací rozhraní .NET Framework jsou napsané v C# nebo Visual Basic, ale můžete také C + +/ CLI ( `/clr` – možnost kompilátoru v jazyce Visual C++). Doporučujeme použít C + +/ CLI pro vrstvu minimální spolupráce v větší aplikace, která zahrnuje spravovaného a nativního kódu.

##  <a name="BK_WindowsUniversal"></a> Univerzální aplikace pro Windows

S Windows 10 aplikace je možné spouštět na všech zařízeních Windows 10, jako jsou tablety a mobilní telefony, stejně jako v klientských počítačích. Na ploše, je možné spouštět jako okno klasické pracovní plochy, ne vždy spuštěný celou obrazovku. Tyto aplikace můžete spustit také na Xboxu a v budoucích zařízení.  Programovací model pro oba typy aplikací se liší od aplikací klasické pracovní plochy systému Win32. Tyto aplikace Windows běží na Windows Runtime, která poskytuje prvky uživatelského rozhraní, základní služby pro tyto aplikace a poskytuje, a rozhraní do různých hardwarových zařízení, které jsou podporovány. Tyto aplikace kompilovány do nativního kódu a mají XAML uživatelské rozhraní nebo používají rozhraní DirectX. Můžete také napsat komponenty prostředí Windows Runtime v nativním kódu, které využívají jiné aplikace Windows – patří mezi ně aplikace, které jsou napsané v C#, Visual Basic nebo JavaScript. Další informace najdete v tématu [vytvoření aplikace pro UPW "Hello world" v jazyce C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp), [vytvořit jednoduché hře pro UPW s rozhraním DirectX](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game), a [součástí vytváření prostředí Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

> [!TIP]
> Pro Windows 10 můžete použít Desktop App Converter Pokud chcete zabalit desktopové aplikace pro nasazení přes Microsoft Store. Další informace najdete v tématu [pomocí modulu Runtime Visual C++ v projektu Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) a [přeneste svoje aplikace klasické pracovní plochy pro Universal Windows platformy (UPW) s přemostění na Desktop](https://msdn.microsoft.com/windows/uwp/porting/desktop-to-uwp-root).

Ukázky pro univerzální platformu Windows najdete v tématu [Windows Universal ukázky na Githubu](https://github.com/Microsoft/Windows-universal-samples)

Pokud máte stávající projekt Windows 8.1 a chcete přenést do Windows 10, najdete v článku [přenos aplikací do univerzální platformy Windows](../porting/porting-to-the-universal-windows-platform-cpp.md). Pokud máte existující classic Win32 klasické pracovní plochy knihovny a kód, který chcete integrovat do aplikace pro UPW, naleznete v tématu [postupy: použití existujícího kódu C++ v aplikaci univerzální platformy Windows](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md).

Další informace o UPW obecné naleznete v tématu [co je aplikace pro univerzální platformu Windows (UPW)?](/windows/uwp/get-started/whats-a-uwp).

Další informace o všech těchto konceptů, najdete v části [Průvodce univerzálních aplikací pro Windows](http://go.microsoft.com/fwlink/p/?linkid=534605).

##  <a name="BK_Native"></a> Počítače a serverové aplikace

Seznamte se se základy psaní klientských aplikací Windows pro desktop, najdete v článku [vývoj aplikací pro Windows v jazyce C++](https://msdn.microsoft.com/vstudio//hh304489) a [Úvod do Windows programování v jazyce C++](https://msdn.microsoft.com/library/windows/desktop/ff381398\(v=vs.85\).aspx).

Ve Windows 10 můžete použít Visual C++ k vytvoření mnoha typů desktopových aplikací:

- Aplikace a nástroje příkazového řádku. Další informace najdete v tématu [konzolové aplikace](../windows/console-applications-in-visual-cpp.md).

- Zákaznické aplikace, které mají propracovanou podobu grafického uživatelského rozhraní. Další informace najdete v tématu [Hilo: vývoj aplikací C++ pro Windows](http://go.microsoft.com/fwlink/p/?LinkId=256417)

- Enterprise a obchodní aplikace, které běží na rozhraní .NET Framework. Většina aplikací rozhraní .NET Framework jsou napsané v C# nebo Visual Basic. Můžete použít C + +/ CLI k vytvoření spolupráce vrstvy, které umožňují kódu .NET do nativních knihoven jazyka C++. Další informace najdete v tématu [.NET programování v jazyce C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

- Klienti SQL databáze, kteří běží v nativním kódu. Další informace najdete v tématu [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

- Doplňky aplikací sady Microsoft Office. Další informace najdete v tématu [sestavování C++ doplňku pro Outlook 2010](http://go.microsoft.com/fwlink/p/?LinkId=256420)

- Ovladače zařízení. Další informace najdete v tématu [Windows Driver Kit (WDK)](http://go.microsoft.com/fwlink/p/?LinkId=256421)

- Služby systému Windows. Další informace najdete v tématu [Úvod do aplikace služby Windows](/dotnet/framework/windows-services/introduction-to-windows-service-applications).

Jazyk Visual C++ umožňuje zabalit téměř jakoukoli vlastní vysoce výkonnou funkcionalitu do Win32 DLL knihoven nebo do knihoven DLL modelu COM, které mohou být zpracovány C++ aplikacemi nebo aplikacemi, které byly napsány v jiných jazycích, například v jazyce C# nebo Visual Basic. Další informace o WIn32 DLL knihovnách naleznete v tématu [knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md). Další informace o vývoji COM najdete v tématu [modelu COM (Component Object)](https://msdn.microsoft.com/library/windows/desktop/ms680573).

## <a name="games"></a>Hry

Hry rozhraní DirectX můžete spustit na PC nebo konzolách Xbox. Další informace najdete v tématu [středisko pro vývojáře rozhraní DirectX](http://go.microsoft.com/fwlink/p/?LinkId=256418).

## <a name="sdks-libraries-and-header-files"></a>Sady SDK, knihovny a soubory hlaviček

Visual C++ obsahuje knihovny Runtime jazyka C (CRT), standardní knihovny C++ a další knihovny specifické pro společnost Microsoft. Zahrnout složky obsahující soubory hlaviček těchto knihoven jsou umístěny v adresáři instalace sady Visual Studio ve složce \VC\ nebo v případě CRT v instalační složce Nástroje sady Windows SDK.

Můžete použít [Správce balíčků Vcpkg](../vcpkg.md) stovky open source knihoven třetích stran jednoduše instalace pro Windows.

Knihovny Microsoft patří:

- Třídy knihovny MFC (Microsoft Foundation Classes): Objektově orientovaný rámec pro vytváření tradičních programů operačního systému Windows (zejména podnikových aplikací), které mají bohatá uživatelská rozhraní obsahující tlačítka, seznamy, stromová zobrazení a další ovládací prvky. Další informace najdete v tématu [desktopových aplikací knihovny MFC](../mfc/mfc-desktop-applications.md).

- Knihovna ATL (Active Template Library): Výkonné pomocné knihovny pro vytváření komponent modelu COM. Další informace najdete v tématu [desktopové komponenty ATL COM](../atl/atl-com-desktop-components.md).

- Knihovna C++ AMP (C++ Accelerated Massive Parallelism): Knihovna, která umožňuje vysoce výkonné obecné výpočetní práce na GPU. Další informace najdete v tématu [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Modul Concurrency Runtime: Knihovna, která zjednodušuje práci paralelního a asynchronního programování pro vícejádrová a mnohojádrová zařízení. Další informace najdete v tématu [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

Mnoho programovacích scénářů pro Windows navíc také vyžaduje sadu Windows SDK obsahující soubory hlaviček, které umožňují přístup ke komponentám operačního systému Windows. Ve výchozím nastavení nainstaluje Visual Studio jako součást sady funkcí C++ Desktop, umožňující vývoj aplikací pro Windows Universal Windows SDK. K vývoji aplikací pro UWP, musíte verzi sady Windows SDK pro Windows 10. Informace najdete v tématu [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk). (Další informace o sady Windows SDK u starších verzí systému Windows, najdete v článku [sady Windows SDK archivu](https://developer.microsoft.com/windows/downloads/sdk-archive)). 

**Program soubory (x86) \Windows Kits** je výchozím umístěním pro všechny verze sady Windows SDK, kterou jste nainstalovali.

Jiné platformy, jako je například konzola Xbox a Azure mají své vlastní sady SDK, které budete pravděpodobně muset nainstalovat. Další informace naleznete ve středisku pro vývojáře DirectX a ve středisku pro vývojáře Azure.

## <a name="development-tools"></a>Nástroje pro vývoj

Systém Visual Studio obsahuje výkonný ladicí program pro nativní kód, nástroje pro statickou analýzu, nástroje pro ladění grafiky, úplný editor kódu, podporu pro testování částí a mnoho dalších nástrojů a pomůcek. Další informace najdete v tématu [začít s vývojem pomocí sady Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio), a [IDE a nástroje pro vývoj](../ide/ide-and-tools-for-visual-cpp-development.md).

## <a name="related-articles"></a>Související články

|Název|Popis|
|-----------|-----------------|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Nadřazené téma pro obsah pro vývojáře v jazyce Visual C++.|