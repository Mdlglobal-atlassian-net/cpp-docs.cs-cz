---
title: Aplikací klasické pracovní plochy (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8e7d3612cd306dc2235b9fb4e6051415cba699c5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569791"
---
# <a name="desktop-applications-visual-c"></a>Aplikací klasické pracovní plochy (Visual C++)
A *desktopová aplikace* v jazyce C++ je nativní aplikace, která přístup úplnou sadu rozhraní API systému Windows a buď běží v okně nebo v systémové konzoly. Aplikací klasické pracovní plochy v jazyce C++ můžete spustit v systému Windows XP do systému Windows 10 (i když je už oficiálně podporované systémem Windows XP a existuje mnoho rozhraní API systému Windows, které byly zavedeny od té doby).

Aplikace se liší od aplikace univerzální platformu Windows (UWP), který můžete spustit na počítačích se systémem Windows 10 a také na XBox, Windows Phone, Surface Hub a dalších zařízení. Další informace o plochy vs. Aplikace UWP, najdete v části [zvolte technologie](https://msdn.microsoft.com/en-us/library/windows/desktop/dn614993\(v=vs.85\).aspx).  


**Plocha most** nastavit ve Windows 10 můžete balíček existující aplikace pracovní plochy nebo objektu COM jako aplikaci UWP a přidat UWP funkce, například touch nebo volání rozhraní API z moderních rozhraní API systému Windows. Aplikace pro UPW můžete také přidat na ploše řešení v sadě Visual Studio a balíček je společně v jedné balíček a používat rozhraní API systému Windows pro komunikaci mezi nimi.  
   
V aplikaci Visual Studio 2017 verze 15,4 a novější můžete vytvořit projekt balíčku aplikace Windows výrazně zjednodušit práci při zabalení aplikace plochy. Několik omezení použít s ohledem na jaké registru volá nebo používá rozhraní API desktopová aplikace, ale v mnoha případech můžete vytvořit alternativní kód cesty k dosažení podobné funkce při spuštění balíčku aplikace. Další informace najdete v tématu [plochy most](/windows-uwp/porting/desktop-to-uwp-root).  
  
 **Terminologie**  
  
-   A *Win32* aplikace je Windows desktopová aplikace v jazyce C++, který můžete použít nativní [rozhraní API systému Windows C nebo API modelu COM.](https://msdn.microsoft.com/en-us/library/windows/desktop/ff818516\(v=vs.85\).aspx) CRT a standardní knihovny rozhraní API a knihovny 3. stran. Aplikace Win32, který spouští v okně vyžaduje vývojáři explicitně pracovat zpráv systému Windows v postupu funkce systému Windows. Bez ohledu název aplikace Win32 mohou být zkompilovány jako (x86) 32bitové nebo 64bitové (x64) binární. V prostředí Visual Studio IDE je shodný s podmínkami x86 a Win32.  
  
-   [Modelu COM (Component Object)](https://msdn.microsoft.com/en-us/library/windows/desktop/ms694363\(v=vs.85\).aspx) je specifikace, která umožňuje programům, které jsou napsané v různých jazycích vzájemnou komunikaci. Mnoho Windows součásti jsou implementované jako objekty modelu COM a použijte standardní pravidla COM pro vytvoření objektu rozhraní zjišťování a objekt odstraňování.  COM – objekty z desktopových aplikací C++ pomocí je relativně jednoduché, ale zápis vlastního objektu COM je složitější. [Active Template Library (ATL)](../atl/atl-com-desktop-components.md) poskytuje makra a pomocných funkcí, které zjednodušují vývoj COM.  
  
-   Aplikace MFC je aplikace pro počítač systému Windows, použít [Microsoft Foundation třídy](../mfc/mfc-desktop-applications.md) k vytvoření uživatelského rozhraní. Aplikace MFC můžete také použít COM – součásti a také CRT a standardní knihovny rozhraní API. MFC poskytuje obálku objektově orientované dynamické C++ přes okno zpráva smyčky a rozhraní API systému Windows. Výchozí volba pro aplikace je MFC – především typ organizace aplikace – mají velký počet ovládacích prvků uživatelského rozhraní nebo vlastní uživatelské ovládací prvky. MFC poskytuje užitečné pomocné třídy pro Správa oken, serializace, manipulaci s textem, tisku a moderní uživatelské rozhraní prvky, jako jsou například na pásu karet. Účinné s knihovnou MFC byste měli být obeznámeni s Win32.  
  
-   C + +/ CLI aplikací nebo součástí používá rozšíření pro C++ syntaxe (jako povolený specifikací C++) k povolení interakce mezi .NET a nativní kód C ++.  C + +/ CLI aplikace může mít částí, které nativně spustit částí, které běží na rozhraní .NET Framework s přístupem k základní knihovny tříd rozhraní .NET. C + +/ CLI je upřednostňovanou možnost, pokud máte nativního kódu C++, který potřebuje pro práci s kód napsaný v jazyce C# nebo Visual Basic. Je primárně určený pro použití v rozhraní .NET knihovny DLL, ne v uživatelském rozhraní kódu. Další informace najdete v tématu [.NET programování v jazyce C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).  
  
 Všechny plochy aplikace v jazyce C++ můžete použít C Runtime (CRT) a standardní knihovny tříd a funkce, objekty COM a veřejné funkce systému Windows, které se souhrnně označují jako rozhraní API systému Windows. Úvod do aplikací klasické pracovní plochy Windows v jazyce C++, najdete v části [informace do programu pro Windows v jazyce C++](http://go.microsoft.com/fwlink/p/?LinkId=262281).  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|Název|Popis|  
|-----------|-----------------|  
|[Konzolové aplikace](../windows/console-applications-in-visual-cpp.md)|Obsahuje informace o konzolových aplikacích. Konzolové aplikace Win32 (nebo Win64) má žádné okno a žádná zpráva smyčky. Spustí se v okně konzoly a vstup a výstup se provádí prostřednictvím příkazového řádku.|  
|[Aplikace pracovní plochy Windows](../windows/windows-desktop-applications-cpp.md)|Postup vytvoření aplikací klasické pracovní plochy, které běží v systému windows a konzole.|  
|[Prostředky pro vytvoření hry s použitím rozhraní DirectX (C++)](../windows/resources-for-creating-a-game-using-directx.md)|Odkazy na obsah pro vytvoření hry v jazyce C++.|  
|[Návod: Vytvoření a použití statické knihovny](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|Postup vytvoření binární soubor LIB.|  
|[Postupy: Použití sady Windows 10 SDK v desktopové aplikaci Windows](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Obsahuje kroky pro nastavení projektu pro sestavení pomocí Windows 10 SDK.|  
  
## <a name="related-articles"></a>Související články  
  
|Název|Popis|  
|-----------|-----------------|  
|[Vývoj pro Windows](http://go.microsoft.com/fwlink/p/?LinkId=262282)|Obsahuje informace o rozhraní API a modelu COM systému Windows. (Některá rozhraní API systému Windows a knihovny DLL třetích stran jsou implementovány jako objekty modelu COM.)|  
|[Hilo: Vývoj aplikací C++ pro systém Windows 7](http://go.microsoft.com/fwlink/p/?LinkId=262284)|Popisuje, jak vytvořit aplikaci plochy plně funkčního klienta systému Windows, která používá Windows animace a Direct2D vytvořit na základě karuselu uživatelské rozhraní.  V tomto kurzu nebyl aktualizován od Windows 7, ale stále poskytuje důkladné Úvod do Win32 programování.|  
|[Visual C++](../visual-cpp-in-visual-studio.md)|Popisuje klíčové funkce jazyka Visual C++ v systému Visual Studio a odkazy na zbytek dokumentace k jazyku Visual C++.|  
  
## <a name="see-also"></a>Viz také  
 [Visual C++](../visual-cpp-in-visual-studio.md)
