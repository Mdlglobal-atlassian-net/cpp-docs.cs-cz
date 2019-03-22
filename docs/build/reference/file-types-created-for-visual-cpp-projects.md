---
title: Typy souborů vytvořených pro projekty Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- header files [C++], Visual Studio projects
- ActiveX controls [C++], Help files
- def files
- project items [C++], files
- Visual Studio C++ projects, files and directories
- resource files, created by wizard
- files [C++], extensions
- Help files, for ActiveX controls
- Web projects [C++], adding items
- .def files
- licensing ActiveX controls
ms.assetid: 2b0ee2e0-ae81-4185-9bb9-11da3c99a283
ms.openlocfilehash: 7ef8127b829b60d84af72874292c33ae1c7c4636
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2019
ms.locfileid: "58327578"
---
# <a name="file-types-created-for-visual-studio-c-projects"></a>Typy souborů vytvořených pro projekty C++ pro Visual Studio

Toto téma popisuje všechny typy souborů, které jsou spojeny s projekty aplikace Visual Studio pro klasické desktopové aplikace. Skutečné soubory zahrnuté ve vašem projektu závisí na typu projektu a možnostech, které jste vybrali při používání průvodce.

- [Soubory projektu a řešení](project-and-solution-files.md)

- [Projekty CLR](files-created-for-clr-projects.md)

- [Program knihovny ATL nebo zdroj ovládacího prvku a soubory hlaviček](atl-program-or-control-source-and-header-files.md)

- [Program knihovny MFC nebo zdroj ovládacího prvku a soubory hlaviček](mfc-program-or-control-source-and-header-files.md)

- [Předkompilované soubory hlaviček](../creating-precompiled-header-files.md)

- [Soubory prostředků](resource-files-cpp.md)

- [Soubory nápovědy (WinHelp)](help-files-winhelp.md)

- [Soubory pokynů](hint-files.md)

Když vytvoříte projekt sady Visual Studio, vytvoření nového řešení, nebo může přidání objektu project do řešení. Rozsáhlé aplikace obecně jsou vyvíjeny pomocí více projektů v řešení.

Projekty vytvářejí obvykle buď aplikace EXE nebo knihovny DLL. Projekty mohou být závislé na sobě navzájem; prostředí sady Visual Studio během procesu sestavení, zkontroluje závislosti uvnitř i mezi projekty. Každý projekt obsahuje základní zdrojový kód a v závislosti na typ projektu, může mít mnoho souborů obsahující různé aspekty projektu. Obsah těchto souborů jsou označeny příponu souboru. Vývojové prostředí sady Visual Studio používá přípony souborů k určení způsobu zpracování obsahu souborů během sestavování.

Následující tabulka uvádí běžné soubory v projektu sady Visual Studio a identifikuje jejich přípony souboru.

|Přípona souboru|Type|Obsah|
|--------------------|----------|--------------|
|asmx|Zdroj|Nasazení souboru.|
|.asp|Zdroj|Stránka ASP.|
|.atp|Project|Soubor šablony projektu aplikace.|
|.bmp, .dib, .gif, .jpg, .jpe, PNG|Prostředek|Obecné obrazových souborů.|
|.bsc|Kompilace|Soubor kódu prohlížeče.|
|.cpp, .c|Zdroj|Soubory hlavní zdrojového kódu pro vaši aplikaci.|
|.cur|Prostředek|Rastrový obrázek kurzoru.|
|.dbp|Project|Soubor projektu databáze.|
|.disco|Zdroj|Dynamicky zpřístupněný soubor dokumentu. Zpracovává zjišťování XML webové služby.|
|.exe, .dll|Project|Soubory knihoven DLL nebo spustitelného souboru.|
|.h|Zdroj|Záhlaví (zahrnout) souboru.|
|htm, HTML, .xsp, ASP, HTC, HTA, .xml|Prostředek|Běžné webové soubory.|
|.HxC|Project|Projekt soubor nápovědy.|
|.ico|Prostředek|Rastrový obrázek ikony.|
|.idb|Kompilace|Stav soubor obsahující informace o závislostech mezi zdrojovými soubory a definice tříd, které je možné použít kompilátor během minimálního opětovného sestavení a přírůstková kompilace. Použití [/Fd](fd-program-database-file-name.md) – možnost kompilátoru zadat název souboru IDB. Zobrazit [/Gm (povolení minimálního opětovného sestavení)](gm-enable-minimal-rebuild.md) Další informace.|
|IDL|Kompilace|Soubor definice jazyka rozhraní. Zobrazit [soubor Interface Definition (IDL)](/windows/desktop/Rpc/the-interface-definition-language-idl-file) v sadě Windows SDK pro další informace.|
|.ilk|Propojení|Soubor přírůstkové propojení. Zobrazit [/INCREMENTAL](incremental-link-incrementally.md) Další informace.|
|.map|Propojení|Textový soubor obsahující informace linkeru. Použití [/Fm](fm-name-mapfile.md) pojmenovat soubor mapování – možnost kompilátoru. Zobrazit [/MAP](map-generate-mapfile.md) Další informace.|
|.mfcribbon-ms|Prostředek|Soubor prostředků, která obsahuje kód XML, který definuje tlačítka, ovládací prvky a atributy pásu karet. Další informace najdete v tématu [Návrhář pásu karet (MFC)](../../mfc/ribbon-designer-mfc.md).|
|obj, .o||Objektové soubory zkompilovány, ale není propojená.|
|.pch|Ladit|Soubor předkompilované hlavičky.|
|.rc, .rc2|Prostředek|[Soubory skriptu prostředků](../../windows/working-with-resource-files.md) pro generování prostředků.|
|.sbr|Kompilace|Zprostředkující soubor zdrojového prohlížeče. Vstupní soubor pro [BSCMAKE](bscmake-options.md).|
|.sln|Řešení|[Řešení](/visualstudio/ide/solutions-and-projects-in-visual-studio) souboru.|
|.suo|Řešení|Soubor možností řešení.|
|.txt|Prostředek|Textový soubor, obvykle v souboru "readme".|
|.Vap|Project|Soubor projektu Visual Studio Analyzer.|
|.vbg|Řešení|Soubor projektu kompatibilní skupiny.|
|.VBP, .vip, .vbproj|Project|Soubor projektu jazyka Visual Basic.|
|.vcxitems|Project|Projekt sdílené položky ke sdílení souborů kód mezi více projekty C++. Zobrazit [soubory projektu a řešení](project-and-solution-files.md) Další informace.|
|.vcxproj|Project|Soubor projektu sady Visual Studio. Zobrazit [soubory projektu a řešení](project-and-solution-files.md) Další informace.|
|.vcxproj.filters|Project|Pokud Průzkumník řešení se používá k přidání souboru do projektu, soubor filtrů definuje kde ve stromovém zobrazení Průzkumníka řešení se přidá soubor, na základě jeho přípony názvu souboru.|
|.vdproj|Project|Soubor projektu nasazení sady Visual Studio.|
|.VMX|Project|Makro souboru projektu.|
|.Vup|Project|Soubor projektu nástroje.|

Informace o dalších soubory přidružené k sadě Visual Studio, naleznete v tématu [typy souborů a přípony souborů v sadě Visual Studio .NET](/visualstudio/ide/reference/project-and-solution-file-types).

Soubory projektu jsou uspořádány do složek v Průzkumníku řešení. Visual Studio vytvoří složku pro zdrojové soubory, soubory hlaviček a soubory prostředků, ale můžete změnit uspořádání těchto složek nebo vytvořit nové. Složky slouží k uspořádání explicitně logických skupin souborů v rámci hierarchie projektu. Může například vytváření složek tak, aby obsahovala všechny zdrojové soubory uživatelského rozhraní, nebo specifikace, dokumentaci, nebo testovacím sadám. Názvy souborů musí být jedinečné.

Při přidání položky do projektu přidat položku do všechny konfigurace pro tento projekt, bez ohledu na to, zda je položka sestavitelná. Například pokud máte projekt s názvem MyProject přidání položky přidá ji do i konfigurace Debug a Release projektu.

## <a name="see-also"></a>Viz také

[Vytváření a správa projektů sady Visual Studio C++](../creating-and-managing-visual-cpp-projects.md)<br>
[Typy projektů C++ v sadě Visual Studio](visual-cpp-project-types.md)<br>