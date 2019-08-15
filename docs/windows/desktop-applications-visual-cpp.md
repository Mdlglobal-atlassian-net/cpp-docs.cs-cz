---
title: Aplikace klasické pracovní plochy C++(Visual)
ms.date: 07/28/2019
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
ms.openlocfilehash: 355102d9d58a8d93d7fb6935528f8fb8c4b534b1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514752"
---
# <a name="desktop-applications-visual-c"></a>Aplikace klasické pracovní plochy C++(Visual)

*Desktopová aplikace* v C++ systému je nativní aplikace, která má přístup k celé sadě rozhraní API systému Windows a buď se spouští v okně, nebo v systémové konzole. Aplikace klasické pracovní C++ plochy v nástroji můžou běžet v systému Windows XP prostřednictvím systému Windows 10 (i když systém Windows XP již není oficiálně podporován a existuje mnoho rozhraní API systému Windows, které bylo od té doby zavedeno). 

Desktopová aplikace se liší od aplikace Univerzální platforma Windows (UWP), která se dá spustit na počítačích s Windows 10, a taky na zařízeních XBox, Windows Phone, Surface Hub a dalších. Další informace o desktopu vs. Aplikace UWP najdete v tématu [Volba vaší technologie](/windows/win32/choose-your-technology).

### <a name="desktop-bridge"></a>Most pro stolní počítače

Ve Windows 10 můžete zabalit stávající desktopovou aplikaci nebo objekt COM jako aplikaci UWP a přidat funkce UWP, jako je dotykové ovládání, nebo volat rozhraní API z moderní sady Windows API. Aplikaci pro UWP můžete také přidat do řešení pro stolní počítače v aplikaci Visual Studio a zabalit je do jednoho balíčku a použít rozhraní API systému Windows ke komunikaci mezi nimi.

V aplikaci Visual Studio 2017 verze 15,4 a novější můžete vytvořit projekt balíčku aplikace systému Windows, který výrazně zjednodušuje práci s balíčkem stávající aplikace klasické pracovní plochy. S ohledem na to, jaká volání registru nebo rozhraní API vaše aplikace klasické pracovní plochy používá, platí několik omezení, ale v mnoha případech můžete vytvořit alternativní cesty kódu pro dosažení podobných funkcí při spuštění v balíčku aplikace. Další informace najdete v tématu [most pro stolní počítače](/windows/uwp/porting/desktop-to-uwp-root).

### <a name="terminology"></a>Terminologie

- Aplikace *Win32* je desktopová aplikace pro C++ Windows, která umožňuje používat nativní rozhraní API pro Windows C nebo rozhraní API [modelu COM](/windows/win32/apiindex/windows-api-list) CRT a standardní knihovny API a knihovny třetích stran. Aplikace Win32, která běží v okně, vyžaduje, aby vývojář pracoval explicitně se zprávami systému Windows v rámci funkce procedury systému Windows. Bez ohledu na název může být aplikace Win32 kompilována jako 32 (x86) nebo 64-bit (x64) binární. V integrovaném vývojovém prostředí sady Visual Studio jsou výrazy x86 a Win32 synonymně.

- [Component Object Model (com)](/windows/win32/com/the-component-object-model) je specifikace, která umožňuje programům napsaným v různých jazycích komunikovat mezi sebou. Mnohé součásti systému Windows jsou implementovány jako objekty modelu COM a následují standardní pravidla modelu COM pro vytváření objektů, zjišťování rozhraní a zničení objektů.  Použití objektů COM z C++ desktopových aplikací je relativně jasné, ale psaní vlastního objektu com je pokročilejší. [Knihovna ATL (Active Template Library)](../atl/atl-com-desktop-components.md) poskytuje makra a pomocné funkce, které zjednodušují vývoj v modelu COM.

- Aplikace MFC je desktopová aplikace pro Windows, která k vytvoření uživatelského rozhraní používá [základní třídy Microsoft](../mfc/mfc-desktop-applications.md) . Aplikace MFC může také používat komponenty modelu COM i CRT a standardní knihovny rozhraní API. Knihovna MFC poskytuje pro C++ smyčku zpráv okna a rozhraní Windows API tenké objekty orientované na objekt. Knihovna MFC je výchozí volbou pro aplikace – zejména podnikové aplikace, které mají velké množství ovládacích prvků uživatelského rozhraní nebo vlastních uživatelských ovládacích prvků. Knihovna MFC poskytuje pohodlné pomocné třídy pro správu oken, serializaci, manipulaci s textem, tisk a prvky moderního uživatelského rozhraní, jako je například pás karet. Aby bylo možné s knihovnou MFC platit, měli byste být obeznámeni s Win32.

- Aplikace C++nebo komponenta/CLI používá rozšíření pro C++ syntaxi ( C++ standardně povoleno) k umožnění interakce mezi .NET a nativním kódem C + +.  Aplikace C++/CLI může mít části, které jsou spouštěny nativně, a části, které jsou spouštěny na .NET Framework s přístupem k knihovně tříd .NET Base. C++/CLI je upřednostňovanou možností, když máte nativní C++ kód, který potřebuje pracovat s kódem napsaným v C# nebo Visual Basic. Je určena pro použití v knihovně DLL .NET, nikoli v kódu uživatelského rozhraní. Další informace najdete v tématu [programování .NET s C++/CLI (vizuál C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

Každá desktopová aplikace C++ v nástroji může používat modul C runtime (CRT) a standardní třídy knihovny a funkce, objekty COM a veřejné funkce systému Windows, které jsou souhrnně označovány jako rozhraní Windows API. Úvodní informace o desktopových aplikacích v systému C++Windows najdete v tématu Začínáme [s Win32 C++a ](/windows/win32/LearnWin32/learn-to-program-for-windows).

## <a name="in-this-section"></a>V tomto oddílu

|Název|Popis|
|-----------|-----------------|
|[Konzolové aplikace pro Windows v C++](console-applications-in-visual-cpp.md)|Obsahuje informace o konzolových aplikacích. Konzolová aplikace Win32 (nebo win64) nemá žádná vlastní okna a žádnou smyčku zpráv. Spustí se v okně konzoly a vstup a výstup se provádí prostřednictvím příkazového řádku.|
|[Návod: Vytváření desktopových aplikací Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Vytvořte jednoduchou desktopovou aplikaci pro Windows.|
|[Vytvoření prázdné desktopové aplikace Windows](creating-an-empty-windows-desktop-application.md)|Jak vytvořit desktopový projekt pro Windows, který nemá žádné výchozí soubory.|
|[Přidávání souborů do prázdných aplikací Win32](adding-files-to-an-empty-win32-applications.md)|Postup přidání souborů do prázdného projektu.|
|[Práce se zdrojovými soubory](working-with-resource-files.md)|Postup přidání obrázků, ikon, tabulek řetězců a dalších prostředků do aplikace klasické pracovní plochy.|
|[Prostředky pro vytvoření hry s použitím rozhraní DirectXC++()](resources-for-creating-a-game-using-directx.md)|Obsahuje odkazy na obsah pro vytváření her C++v nástroji.|
|[Návod: Vytvoření a použití statické knihovny](walkthrough-creating-and-using-a-static-library-cpp.md)|Postup vytvoření binárního souboru. lib.|
|[Postupy: Použití sady Windows 10 SDK v desktopové aplikaci Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Obsahuje kroky pro nastavení projektu pro sestavení pomocí sady Windows 10 SDK.|

## <a name="related-articles"></a>Související články

|Název|Popis|
|-----------|-----------------|
|[Vývoj pro Windows](/windows/win32/index)|Obsahuje informace o rozhraní API a modelu COM systému Windows. (Některá rozhraní API systému Windows a knihovny DLL třetích stran jsou implementovány jako objekty modelu COM.)|
|[Hilo Vývoj C++ aplikací pro systém Windows 7](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)|Popisuje, jak vytvořit bohatou klientskou aplikaci pro Windows, která používá animaci Windows a Direct2D k vytvoření uživatelského rozhraní založeného na karuselu.  Tento kurz se od Windows 7 neaktualizoval, ale stále poskytuje důkladný úvod k programování v systému Win32.|
|[Přehled programování v C++ v systému Windows](overview-of-windows-programming-in-cpp.md)|Popisuje klíčové funkce programování pro stolní počítače v C++systému Windows.|

## <a name="see-also"></a>Viz také:

[C++ v sadě Visual Studio](../overview/visual-cpp-in-visual-studio.md)