---
title: Typy vytvořené pro projekty Visual C++ souborů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- header files [C++], Visual C++ projects
- ActiveX controls [C++], Help files
- def files
- project items [C++], files
- Visual C++ projects, files and directories
- resource files, created by wizard
- files [C++], extensions
- Help files, for ActiveX controls
- Web projects [C++], adding items
- .def files
- licensing ActiveX controls
ms.assetid: 2b0ee2e0-ae81-4185-9bb9-11da3c99a283
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7158e729d80d8b0456862ee6418f039b7f948fe
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33336014"
---
# <a name="file-types-created-for-visual-c-projects"></a>Typy souborů vytvořených pro projekty Visual C++
Toto téma popisuje všechny typy souborů, které jsou spojeny s projekty Visual C++ pro classic aplikací klasické pracovní plochy. Skutečné soubory obsažené v projektu závisí na typu projektu a možností, které jste vybrali při použití průvodce.  
  
-   [Soubory projektu a řešení](../ide/project-and-solution-files.md)  
  
-   [CLR – projekty](../ide/files-created-for-clr-projects.md)  
  
-   [Program knihovny ATL nebo zdroj ovládacího prvku a soubory hlaviček](../ide/atl-program-or-control-source-and-header-files.md)  
  
-   [Program knihovny MFC nebo zdroj ovládacího prvku a soubory hlaviček](../ide/mfc-program-or-control-source-and-header-files.md)  
  
-   [Předkompilované soubory hlaviček](../ide/precompiled-header-files.md)  
  
-   [Soubory prostředků](../ide/resource-files-cpp.md)  
  
-   [Soubory nápovědy (WinHelp)](../ide/help-files-winhelp.md)  
  
-   [Soubory pokynů](../ide/hint-files.md)  
  
 Pokud jste [vytvoření projektu Visual C++](../ide/creating-desktop-projects-by-using-application-wizards.md), je možné vytvořit nové řešení, nebo může být přidání projektu k řešení. Rozsáhlé aplikace jsou běžně vyvinuté s více projekty v řešení.  
  
 Projekty obvykle vytvářejí EXE nebo knihovny DLL. Projekty může být závislá na sobě navzájem; během procesu sestavení prostředí Visual C++ kontroluje závislosti uvnitř i mezi projekty. Každý projekt má základní zdrojový kód a v závislosti na druhu projektu, může mít mnoho souborů obsahujících různé aspekty projektu. Obsah tyto soubory jsou vypsány přípona souboru. Vývojové prostředí sady Visual Studio používá přípony souborů k určení způsobu zpracování obsahu souboru během sestavení.  
  
 Následující tabulka uvádí běžné soubory v projektu jazyka Visual C++ a identifikuje je jejich příponu souboru.  
  
|Přípona souboru|Typ|Obsah|  
|--------------------|----------|--------------|  
|.asmx|Zdroj|Soubor nasazení.|  
|.asp|Zdroj|Stránka ASP.|  
|.ATP|Projekt|Soubor projektu šablony aplikace.|  
|GIF, BMP, DIB, JPG, JPE, .png|Prostředek|Obecné obrázkové soubory.|  
|.BSC|Kompilace|K souboru kódu prohlížeče.|  
|Sada; .c|Zdroj|Soubory hlavní zdrojového kódu pro vaši aplikaci.|  
|.cur|Prostředek|Rastrový obrázek kurzoru.|  
|.DBP|Projekt|Soubor projektu databáze.|  
|.disco|Zdroj|Dynamické zjišťování souboru dokumentu. Zpracovává zjišťování XML webové služby.|  
|.exe, .dll|Projekt|Soubory spustitelný soubor nebo dynamické knihovny.|  
|.h|Zdroj|Záhlaví (zahrnout) souboru.|  
|htm, HTML, .xsp, .asp, HTC, HTA, .xml|Prostředek|Běžné webové soubory.|  
|. HxC|Projekt|Soubor nápovědy projektu.|  
|.ico|Prostředek|Rastrový obrázek ikony.|  
|IDB|Kompilace|Stav soubor obsahující informace o závislostech mezi zdrojové soubory a definice tříd, které se dají použít kompilátorem během minimální opětovné sestavení a přírůstkové kompilace. Použití [/Fd](../build/reference/fd-program-database-file-name.md) – možnost kompilátoru k zadání názvu souboru IDB. V tématu [/Gm (povolit minimální sestavení)](../build/reference/gm-enable-minimal-rebuild.md) Další informace.|  
|.IDL|Kompilace|Soubor definice jazyka rozhraní. V tématu [soubor definice IDL (Interface)](http://msdn.microsoft.com/library/windows/desktop/aa378712) ve Windows SDK pro další informace.|  
|.ilk|Propojení|Soubor přírůstkové odkazu. V tématu [/PŘÍRŮSTKOVÉ](../build/reference/incremental-link-incrementally.md) Další informace.|  
|.map|Propojení|Textový soubor obsahující informace linkeru. Použití [/Fm](../build/reference/fm-name-mapfile.md) – možnost kompilátoru k názvu souboru. V tématu [/MAP](../build/reference/map-generate-mapfile.md) Další informace.|  
|.mfcribbon-ms|Prostředek|Soubor prostředků, který obsahuje kód XML, který definuje tlačítka, ovládací prvky a atributy na pásu karet. Další informace najdete v tématu [Návrhář pásu karet (MFC)](../mfc/ribbon-designer-mfc.md).|  
|.obj, .o||Soubory objektů, kompilovat, ale nejsou spojeny.|  
|.pch|Ladit|Předkompilované soubory hlaviček|  
|.rc, .rc2|Prostředek|[Soubory skriptu prostředků](../windows/working-with-resource-files.md) sloužící ke generování prostředků.|  
|.SBR|Kompilace|Pomocný soubor zdroj prohlížeče. Vstupní soubor pro [BSCMAKE](../build/reference/bscmake-options.md).|  
|.sln|Řešení|[Řešení](http://msdn.microsoft.com/en-us/a45c299d-69f5-4b67-879d-1383417df0a7) souboru.|  
|.suo|Řešení|Soubor možností řešení.|  
|.txt|Prostředek|Textový soubor, obvykle soubor "readme".|  
|.Vap|Projekt|Soubor projektu Visual Studio Analyzer.|  
|.vbg|Řešení|Soubor skupiny kompatibilní projektu.|  
|.VBP, .vip, .vbproj|Projekt|Soubor projektu jazyka Visual Basic.|  
|.vcxitems|Projekt|Sdílené položky projektu pro sdílení souborů kód mezi více projektů C++. V tématu [soubory projektu a soubory pravidel](../ide/project-and-solution-files.md) Další informace.|
|VCXPROJ|Projekt|Soubor projektu Visual C++. V tématu [soubory projektu a soubory pravidel](../ide/project-and-solution-files.md) Další informace.|  
|. vcxproj.filters|Projekt|Když Průzkumník řešení se používá k přidání souboru do projektu, soubor filtry definuje kde ve stromovém zobrazení Průzkumník řešení se přidá soubor, na základě jeho přípony názvu souboru.|  
|.vdproj|Projekt|Soubor projektu nasazení sady Visual Studio.|  
|VMX|Projekt|Makro souboru projektu.|  
|.Vup|Projekt|Soubor projektu nástroje.|  
  
 Informace na jiné soubory přidružené k sadě Visual Studio najdete v tématu [typy souborů a přípony souborů v sadě Visual Studio .NET](/visualstudio/ide/reference/project-and-solution-file-types).  
  
 Soubory projektu jsou uspořádány do složky v Průzkumníku řešení. Visual C++ vytvoří složku pro zdrojové soubory, soubory hlaviček a soubory prostředků, ale můžete změnit uspořádání těchto složek nebo vytvořit nové. Složky můžete použít k uspořádání explicitně logických skupin souborů v rámci hierarchie projektu. Můžete například vytvořit složky tak, aby obsahovala všechny uživatele rozhraní zdrojové soubory, nebo specifikace, dokumentace, nebo sady testů. Názvy souborů musí být jedinečné.  
  
 Pokud položku přidáte do projektu, přidejte položku do všechny konfigurace pro tento projekt, bez ohledu na to, zda je položka sestavitelná. Například pokud máte projekt s názvem MyProject, přidání položky přidává ji k ladění a vydání konfigurace se projektu.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření a správa projektů Visual C++](../ide/creating-and-managing-visual-cpp-projects.md)   
 [Typy projektů Visual C++](../ide/visual-cpp-project-types.md)   
 [Podpora průvodce pro ostatní jazyky](../ide/wizard-support-for-other-languages.md)