---
title: Desktopové aplikace (Visual C++)
ms.date: 11/04/2016
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
ms.openlocfilehash: 090180062139642d8a686e9f1bf063f3e65aee88
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58771916"
---
# <a name="desktop-applications-visual-c"></a>Desktopové aplikace (Visual C++)

A *aplikace klasické pracovní plochy* v jazyce C++ je nativní aplikace s přístupem k kompletní sadu rozhraní API pro Windows a buď spuštěn v okně nebo systémové konzoly. Desktopové aplikace v jazyce C++ může běžet na Windows XP do systému Windows 10 (i když je již nejsou oficiálně podporované Windows XP a existuje mnoho rozhraní API Windows, které byly zavedeny od té doby).

Desktopová aplikace, která se liší od aplikace univerzální platformy Windows (UPW), které můžou spouštět na počítačích se systémem Windows 10 a také na XBox, Windows Phone, Surface Hubech a dalších zařízení. Další informace o klasické pracovní plochy vs. Aplikace UWP, naleznete v tématu [výběr technologie](/windows/desktop/choose-your-technology).

### <a name="desktop-bridge"></a>Přemostění na Desktop

Ve Windows 10 můžete zabalit existující aplikace klasické pracovní plochy nebo objekt modelu COM jako aplikace pro UPW a přidat UPW funkce, jako je touch nebo volání rozhraní API ze sady moderní rozhraní Windows API. Můžete také přidat aplikace pro UPW pro desktop řešení v sadě Visual Studio a balíček je společně v jednom balíčku a používat rozhraní Windows API pro komunikaci mezi nimi.

V sadě Visual Studio 2017 verze 15.4 nebo novější můžete vytvořit projekt Windows Application balíček výrazně zjednodušit práci při balení aplikace klasické pracovní plochy. S ohledem na jaké registru volá platí několik omezení nebo používá rozhraní API pro aplikace klasické pracovní plochy, ale v mnoha případech můžete vytvořit kód alternativní cesty dosáhnout podobné funkce jako při spuštění v balíčku aplikace. Další informace najdete v tématu [přemostění na Desktop](/windows-uwp/porting/desktop-to-uwp-root).

### <a name="terminology"></a>Terminologie

- A *Win32* aplikace je Windows aplikace klasické pracovní plochy v jazyce C++, který může používat nativní [rozhraní API Windows C a/nebo rozhraní API modelu COM](/windows/desktop/apiindex/windows-api-list) CRT a standardní knihovny rozhraní API a 3. knihovnách třetích stran. Aplikace Win32, na kterém běží v okně vyžaduje pro vývojáře pro práci s zpráv Windows uvnitř procedury funkce Windows explicitně. Bez ohledu na název můžete jako (x86) 32bitové nebo 64bitové (x64) binární zkompilovat aplikaci Win32. V sadě Visual Studio IDE je shodný podmínky x86 a Win32.

- [Modelu COM (Component Object)](/windows/desktop/com/the-component-object-model) je specifikace, které umožňuje programy napsané v různých jazycích, aby mezi sebou komunikovat. Řada Windows komponenty jsou implementovány jako objekty modelu COM a pravidlům standardní modelu COM pro vytváření objektů rozhraní zničení objektu a zjišťování.  Použití objektů COM v aplikacích klasické pracovní plochy jazyka C++ je poměrně přímočarý, ale zápis objektu modelu COM je složitější. [Aktivní šablony knihovny (ATL)](../atl/atl-com-desktop-components.md) poskytuje makra a pomocných funkcí, které zjednodušují vývoj COM.

- Aplikace MFC je desktopová aplikace Windows použít [Microsoft Foundation Classes](../mfc/mfc-desktop-applications.md) k vytvoření uživatelského rozhraní. Aplikace knihovny MFC můžete také použít komponenty modelu COM stejně jako CRT a standardní knihovny rozhraní API. Knihovna MFC poskytuje dynamického zajišťování objektově orientované obálku C++ přes rozhraní Windows API a smyčky zpráv okna. Knihovna MFC je výchozí volbou pro aplikace, zejména ty podnikové aplikace –, které mají velké množství ovládacích prvků uživatelského rozhraní nebo vlastních uživatelských ovládacích prvků. Knihovna MFC poskytuje pohodlné pomocné třídy pro správu okna, serializaci, manipulaci s textem, tisk a prvky moderního uživatelského rozhraní, jako je například pás karet. Účinná s knihovnou MFC měli seznámit s Win32.

- C + +/ CLI aplikace nebo komponenty používá rozšíření syntaxe jazyka C++ (vzhledem k tomu provést ve specifikaci jazyka C++) k povolení interakce mezi rozhraním .NET a nativního kódu jazyka C++.  C + +/ CLI aplikace může mít, na kterých běží nativně díly a, které běží na rozhraní .NET Framework s přístupem k základní knihovny tříd rozhraní .NET. C + +/ CLI je upřednostňovanou možností, když máte nativní kód C++, kterou je potřeba pracovat s kódem napsaným v jazyce C# nebo Visual Basic. Je primárně určena pro použití v knihovnách DLL .NET, nikoli v uživatelském rozhraní kódu. Další informace najdete v tématu [.NET programování v jazyce C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

Všechny aplikace klasické pracovní plochy v jazyce C++ můžete použít C Runtime (CRT) a standardní knihovny třídy a funkce, objekty COM a veřejných funkcí Windows, které jsou souhrnně označovány jako Windows API. Úvod do aplikací klasické pracovní plochy Windows v jazyce C++, naleznete v tématu [Win32 a C++ vám začít](/windows/desktop/LearnWin32/learn-to-program-for-windows).

## <a name="in-this-section"></a>V tomto oddílu

|Název|Popis|
|-----------|-----------------|
|[Konzolové aplikace pro Windows v C++](console-applications-in-visual-cpp.md)|Obsahuje informace o konzolových aplikacích. Konzolová aplikace Win32 (nebo Win64) nemá žádná vlastní okna ani žádnou smyčku zpráv. Spustí se v okně konzoly a vstup a výstup se provádí prostřednictvím příkazového řádku.|
|[Návod: Vytváření desktopových aplikací Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Vytvoření jednoduché aplikace klasické pracovní plochy Windows.|
|[Vytvoření prázdné desktopové aplikace Windows](creating-an-empty-windows-desktop-application.md)|Jak vytvořit projekt klasické pracovní plochy Windows, který nemá žádný výchozí soubory.|
|[Přidávání souborů do prázdných aplikací Win32](adding-files-to-an-empty-win32-applications.md)|Postup přidání souborů do projektu prázdný.|
|[Práce se zdrojovými soubory](working-with-resource-files.md)|Jak přidat obrázky, ikony, tabulek řetězců a dalších prostředků pro aplikace klasické pracovní plochy.|
|[Prostředky pro vytvoření hry s použitím rozhraní DirectX (C++)](resources-for-creating-a-game-using-directx.md)|Obsahuje odkazy na obsah pro vytváření her v C++.|
|[Návod: Vytvoření a použití statické knihovny](walkthrough-creating-and-using-a-static-library-cpp.md)|Jak vytvořit binární soubor LIB.|
|[Postupy: Použití sady Windows 10 SDK v desktopové aplikaci Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Obsahuje kroky pro vytvoření projektu pro sestavení pomocí Windows 10 SDK.|

## <a name="related-articles"></a>Související články

|Název|Popis|
|-----------|-----------------|
|[Vývoj pro Windows](/windows/desktop/index)|Obsahuje informace o rozhraní API a modelu COM systému Windows. (Některá rozhraní API systému Windows a knihovny DLL třetích stran jsou implementovány jako objekty modelu COM.)|
|[Hilo: Vývoj aplikací v jazyce C++ pro Windows 7](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)|Popisuje, jak vytvořit aplikaci klasické pracovní plochy plně funkčním klientovi Windows, která používá k vytvoření kolotočového uživatelského rozhraní Windows Animation a Direct2D.  V tomto kurzu se neaktualizoval od verze Windows 7, ale stále obsahuje důkladný Úvod k programování v systému Win32.|
|[Přehled programování v C++ v systému Windows](overview-of-windows-programming-in-cpp.md)|Popisuje klíčové funkce Windows desktop programování v jazyce C++.|

## <a name="see-also"></a>Viz také

[Visual C++](../overview/visual-cpp-in-visual-studio.md)