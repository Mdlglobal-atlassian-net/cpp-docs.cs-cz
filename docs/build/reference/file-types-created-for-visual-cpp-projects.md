---
title: Soubor typy vytvořené pro sadu Visual Studio C++ projekty
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
ms.openlocfilehash: 42040854b7a038ebe32d67e305c947d095d5391a
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446298"
---
# <a name="file-types-created-for-visual-studio-c-projects"></a>Typy souborů vytvořených pro projekty C++ pro Visual Studio

Mnoho typů souborů jsou spojeny s projekty aplikace Visual Studio pro klasické desktopové aplikace. Skutečné soubory zahrnuté ve vašem projektu závisí na typu projektu a možnostech, které jste vybrali při používání průvodce.

- [Soubory projektu a řešení](project-and-solution-files.md)

- [Projekty CLR](files-created-for-clr-projects.md)

- [Program knihovny ATL nebo zdroj ovládacího prvku a soubory hlaviček](atl-program-or-control-source-and-header-files.md)

- [Program knihovny MFC nebo zdroj ovládacího prvku a soubory hlaviček](mfc-program-or-control-source-and-header-files.md)

- [Předkompilované soubory hlaviček](../creating-precompiled-header-files.md)

- [Soubory prostředků](resource-files-cpp.md)

- [Soubory nápovědy (WinHelp)](help-files-winhelp.md)

- [Soubory pokynů](hint-files.md)

Když vytvoříte projekt sady Visual Studio, můžete například vytvořit v novém řešení nebo projektu můžete přidat do existujícího řešení. Rozsáhlé aplikace obecně jsou vyvíjeny pomocí více projektů v řešení.

Projekty vytvářejí obvykle buď aplikace EXE nebo knihovny DLL. Projekty mohou být závislé na sobě navzájem; prostředí sady Visual Studio během procesu sestavení, zkontroluje závislosti uvnitř i mezi projekty. Každý projekt má obvykle core zdrojového kódu. V závislosti na typ projektu může mít mnoho souborů obsahující různé aspekty projektu. Obsah těchto souborů jsou označeny příponu souboru. Vývojové prostředí sady Visual Studio používá přípony souborů k určení způsobu zpracování obsahu souborů během sestavování.

Následující tabulka uvádí běžné soubory v projektu sady Visual Studio a identifikuje jejich přípony souboru.

|Přípona souboru|Type|Obsah|
|--------------------|----------|--------------|
|asmx|Source|Nasazení souboru.|
|.asp|Source|Stránka ASP.|
|.atp|Project|Soubor šablony projektu aplikace.|
|.bmp, .dib, .gif, .jpg, .jpe, PNG|Resource|Obecné obrazových souborů.|
|.bsc|Kompilace|Soubor kódu prohlížeče.|
|.cpp, .c|Source|Soubory hlavní zdrojového kódu pro vaši aplikaci.|
|.cur|Resource|Rastrový obrázek kurzoru.|
|.dbp|Project|Soubor projektu databáze.|
|.disco|Source|Dynamicky zpřístupněný soubor dokumentu. Zpracovává zjišťování XML webové služby.|
|.exe, .dll|Project|Soubory knihoven DLL nebo spustitelného souboru.|
|.h|Source|Záhlaví (zahrnout) souboru.|
|htm, HTML, .xsp, ASP, HTC, HTA, .xml|Resource|Běžné webové soubory.|
|.HxC|Project|Projekt soubor nápovědy.|
|.ico|Resource|Rastrový obrázek ikony.|
|.idb|Kompilace|Stav soubor obsahující informace o závislostech mezi zdrojovými soubory a definice tříd. Lze použít kompilátor během přírůstková kompilace. Použití [/Fd](fd-program-database-file-name.md) – možnost kompilátoru zadat název souboru IDB.|
|IDL|Kompilace|Soubor definice jazyka rozhraní. Další informace najdete v tématu [soubor Interface Definition (IDL)](/windows/desktop/Rpc/the-interface-definition-language-idl-file) v sadě Windows SDK.|
|.ilk|Propojení|Soubor přírůstkové propojení. Další informace najdete v tématu [/INCREMENTAL](incremental-link-incrementally.md).|
|.map|Propojení|Textový soubor obsahující informace linkeru. Použití [/Fm](fm-name-mapfile.md) pojmenovat soubor mapování – možnost kompilátoru. Další informace najdete v tématu [/MAP](map-generate-mapfile.md).|
|.mfcribbon-ms|Resource|Soubor prostředků, která obsahuje kód XML, který definuje tlačítka, ovládací prvky a atributy MFC na pásu karet. Další informace najdete v tématu [Návrháře pásu karet](../../mfc/ribbon-designer-mfc.md).|
|obj, .o||Objektové soubory zkompilovány, ale není propojená.|
|.pch|Ladit|Soubor předkompilované hlavičky.|
|.rc, .rc2|Resource|[Soubory skriptu prostředků](../../windows/working-with-resource-files.md) pro generování prostředků.|
|.sbr|Kompilace|Zprostředkující soubor zdrojového prohlížeče. Vstupní soubor pro [BSCMAKE](bscmake-options.md).|
|.sln|Řešení|[Řešení](/visualstudio/ide/solutions-and-projects-in-visual-studio) souboru.|
|.suo|Řešení|Soubor možností řešení.|
|.txt|Resource|Textový soubor, obvykle v souboru "readme".|
|.Vap|Project|Soubor projektu Visual Studio Analyzer.|
|.vbg|Řešení|Soubor projektu kompatibilní skupiny.|
|.VBP, .vip, .vbproj|Project|Soubor projektu jazyka Visual Basic.|
|.vcxitems|Project|Projekt sdílené položky ke sdílení souborů kód mezi více projekty C++. Další informace najdete v tématu [soubory projektu a řešení](project-and-solution-files.md).|
|.vcxproj|Project|Soubor projektu sady Visual Studio. Další informace najdete v tématu [soubory projektu a řešení](project-and-solution-files.md).|
|.vcxproj.filters|Project|Při přidání souboru do projektu používáte Průzkumníka řešení. Soubor filtrů definuje where ve stromovém zobrazení Průzkumníka řešení přidáte soubor, na základě jeho přípony názvu souboru.|
|.vdproj|Project|Soubor projektu nasazení sady Visual Studio.|
|.VMX|Project|Makro souboru projektu.|
|.Vup|Project|Soubor projektu nástroje.|

Informace o dalších soubory přidružené k sadě Visual Studio, naleznete v tématu [typy souborů a přípony souborů v sadě Visual Studio .NET](/visualstudio/ide/reference/project-and-solution-file-types).

Soubory projektu jsou uspořádány do složek v Průzkumníku řešení. Visual Studio vytvoří složku pro zdrojové soubory, soubory hlaviček a soubory prostředků, ale můžete změnit uspořádání těchto složek nebo vytvořit nové. Složky slouží k uspořádání explicitně logických skupin souborů v rámci hierarchie projektu. Například můžete vytvořit složky tak, aby obsahovala všechny soubory zdroje uživatelského rozhraní. Nebo složky pro specifikace, dokumentace ke službě nebo testovacím sadám. Názvy souborů musí být jedinečné.

Při přidání položky do projektu přidat položku do všech konfigurací pro daný projekt. Je položka přidána, zda je sestavitelnou nebo ne. Například pokud máte projekt s názvem MyProject přidání položky přidá ji do i konfigurace Debug a Release projektu.

## <a name="see-also"></a>Viz také:

[Vytváření a správa projektů sady Visual Studio C++](../creating-and-managing-visual-cpp-projects.md)<br>
[Typy projektů C++ v sadě Visual Studio](visual-cpp-project-types.md)<br>