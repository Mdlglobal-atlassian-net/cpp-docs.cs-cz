---
title: Typy souborů vytvořených pro projekty sady C++ Visual Studio
ms.date: 04/08/2019
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
ms.openlocfilehash: 078c83a9c95c1b143af2037240d5cc0a16211827
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492874"
---
# <a name="file-types-created-for-visual-studio-c-projects"></a>Typy souborů vytvořených pro projekty sady C++ Visual Studio

Mnoho typů souborů je přidruženo k projektům aplikace Visual Studio pro klasické desktopové aplikace. Skutečné soubory zahrnuté v projektu závisí na typu projektu a možnostech, které jste vybrali při použití průvodce.

- [Soubory projektu a řešení](project-and-solution-files.md)

- [Projekty CLR](files-created-for-clr-projects.md)

- [Program knihovny ATL nebo zdroj ovládacího prvku a soubory hlaviček](atl-program-or-control-source-and-header-files.md)

- [Program knihovny MFC nebo zdroj ovládacího prvku a soubory hlaviček](mfc-program-or-control-source-and-header-files.md)

- [Předkompilované soubory hlaviček](../creating-precompiled-header-files.md)

- [Soubory prostředků](resource-files-cpp.md)

- [Soubory nápovědy (WinHelp)](help-files-winhelp.md)

- [Soubory pokynů](hint-files.md)

Při vytváření projektu sady Visual Studio je možné ho vytvořit v novém řešení nebo můžete přidat projekt do existujícího řešení. Netriviální aplikace jsou běžně vyvíjeny s více projekty v řešení.

Projekty obvykle vytváří buď EXE, nebo knihovnu DLL. Projekty mohou být závislé na sobě navzájem; během procesu sestavování prostředí Visual Studio kontroluje závislosti v rámci i mezi projekty. Každý projekt má obvykle základní zdrojový kód. V závislosti na typu projektu může mít mnoho dalších souborů, které obsahují různé aspekty projektu. Obsah těchto souborů je označen příponou souboru. Vývojové prostředí sady Visual Studio používá přípony souborů k určení způsobu zpracování obsahu souboru během sestavení.

Následující tabulka ukazuje běžné soubory v projektu sady Visual Studio a identifikuje je pomocí jejich přípony souboru.

|Přípona souboru|type|Obsah|
|--------------------|----------|--------------|
|. asmx|Source|Soubor nasazení.|
|.asp|Source|Active Server stránkovací soubor.|
|. ATP|Project|Soubor projektu šablony aplikace|
|. bmp,. DIB,. gif,. jpg,. jpe,. png|Resource|Obecné soubory obrázků.|
|. BSC|Kompilují|Soubor kódu prohlížeče.|
|. cpp,. c|Source|Soubory hlavního zdrojového kódu pro vaši aplikaci.|
|. měna|Resource|Rastrový obrázek kurzoru|
|.dbp|Project|Soubor databázového projektu.|
|.disco|Source|Soubor dokumentu dynamického zjišťování. Zpracovává zjišťování webové služby XML.|
|. exe,. dll|Project|Spustitelné soubory nebo soubory dynamické knihovny.|
|.h|Source|Soubor hlaviček (include).|
|. htm,. html,. webový XSP,. ASP,. HTC,. HTA,. XML|Resource|Běžné webové soubory.|
|. HxC|Project|Soubor projektu help.|
|.ico|Resource|Ikona rastrového obrázku ikony|
|. IDB|Kompilují|Stavový soubor obsahující informace o závislostech mezi zdrojovými soubory a definicemi tříd. Dá se použít kompilátorem během přírůstkové kompilace. Pomocí možnosti kompilátoru [/FD](fd-program-database-file-name.md) zadejte název souboru. IDB.|
|. idl|Kompilují|Soubor jazyka definice rozhraní. Další informace naleznete v tématu [soubor definice rozhraní (IDL)](/windows/win32/Rpc/the-interface-definition-language-idl-file) v Windows SDK.|
|. ilk|Propojení|Soubor přírůstkového propojení. Další informace najdete v tématu [/incremental](incremental-link-incrementally.md).|
|. map|Propojení|Textový soubor obsahující informace linkeru. Pro pojmenování souboru mapy použijte možnost kompilátoru [/FM](fm-name-mapfile.md) . Další informace najdete v tématu [/map](map-generate-mapfile.md).|
|. mfcribbon-ms|Resource|Soubor prostředků, který obsahuje kód XML, který definuje tlačítka, ovládací prvky a atributy knihovny MFC na pásu karet. Další informace najdete v tématu [Návrhář pásu karet](../../mfc/ribbon-designer-mfc.md).|
|. obj,. o||Soubory objektů, kompilovány, ale nejsou propojeny.|
|. pch|Ladění|Soubor předkompilované hlavičky|
|. RC,. RC2|Resource|[Soubory skriptu prostředků](../../windows/working-with-resource-files.md) pro generování prostředků.|
|.sbr|Kompilují|Zprostředkující soubor prohlížeče zdrojového kódu. Vstupní soubor pro [BSCMAKE](bscmake-options.md).|
|.sln|Řešení|Soubor [řešení](/visualstudio/ide/solutions-and-projects-in-visual-studio) .|
|.suo|Řešení|Soubor možností řešení.|
|.txt|Resource|Textový soubor, obvykle soubor Readme.|
|.vap|Project|Soubor projektu Visual Studio Analyzer.|
|.vbg|Řešení|Kompatibilní soubor skupiny projektu.|
|. vbp,. VIP,. vbproj|Project|Soubor projektu Visual Basic.|
|.vcxitems|Project|Projekt sdílených položek pro sdílení souborů kódu mezi několika C++ projekty. Další informace naleznete v tématu [soubory projektu a řešení](project-and-solution-files.md).|
|.vcxproj|Project|Soubor projektu sady Visual Studio. Další informace naleznete v tématu [soubory projektu a řešení](project-and-solution-files.md).|
|. vcxproj. filters|Project|Používá se při použití Průzkumník řešení k přidání souboru do projektu. Soubor filtrů definuje, kde ve stromovém zobrazení Průzkumník řešení přidat soubor na základě přípony názvu souboru.|
|. vdproj|Project|Soubor projektu nasazení sady Visual Studio.|
|. VMX|Project|Soubor projektu makra.|
|.vup|Project|Soubor projektu nástroje.|

Informace o dalších souborech přidružených k aplikaci Visual Studio naleznete v tématu [typy souborů a přípony souborů v aplikaci Visual Studio .NET](/visualstudio/ide/reference/project-and-solution-file-types).

Soubory projektu jsou uspořádány do složek v Průzkumník řešení. Visual Studio vytvoří složku pro zdrojové soubory, soubory hlaviček a soubory prostředků, ale můžete tyto složky změnit uspořádáním nebo vytvořit nové. Složky můžete použít k organizování explicitních logických clusterů souborů v rámci hierarchie projektu. Můžete například vytvořit složky, které budou obsahovat všechny zdrojové soubory uživatelského rozhraní. Nebo složky pro specifikace, dokumentaci nebo sady testů. Všechny názvy složek souborů by měly být jedinečné.

Když přidáte položku do projektu, přidáte položku do všech konfigurací pro daný projekt. Položka je přidána bez ohledu na to, zda je sestavena. Například pokud máte projekt s názvem MyProject, přidání položky přidá do konfigurace ladění a vydávání projektů.

## <a name="see-also"></a>Viz také:

[Vytváření a správa projektů sady C++ Visual Studio](../creating-and-managing-visual-cpp-projects.md)<br>
[Typy projektů C++ Visual Studio](visual-cpp-project-types.md)<br>