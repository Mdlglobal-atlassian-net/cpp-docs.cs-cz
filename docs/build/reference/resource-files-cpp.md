---
title: Zdrojové soubory (C++)
ms.date: 05/14/2019
helpviewer_keywords:
- resource files
- resources [C++]
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
ms.openlocfilehash: 20e57aa51cff8c4e3392c313645468387c2a4244
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707394"
---
# <a name="resource-files-c"></a>Zdrojové soubory (C++)

Prostředky jsou prvky rozhraní, které poskytují informace o uživateli. Rastrové obrázky, ikony, panely nástrojů a kurzory jsou všechny prostředky. Některé prostředky můžete provádět akce, jako je výběr z nabídky nebo zadávání dat v dialogovém okně.

 Další informace najdete v tématu [práci s nimi](../../windows/working-with-resource-files.md).

|Název souboru|Umístění adresáře|Umístění v Průzkumníku řešení|Popis|
|---------------|------------------------|--------------------------------|-----------------|
|*Název_projektu*.rc|*Projname*|Zdrojové soubory|Soubor skriptu prostředků pro projekt. Soubor skriptu prostředků obsahuje následující příkaz, v závislosti na typu projektu a vybrané podpory pro projekt (například panely nástrojů, dialogová okna nebo HTML):<br /><br />– Definice výchozí nabídky.<br />– Tabulky akcelerátoru a řetězců.<br />– Výchozí **o** dialogové okno.<br />-Další dialogová okna.<br />-Soubor ikony (res\\*název_projektu*ICO).<br />-Informace o version.<br />-Rastrových obrázků.<br />-Panel nástrojů.<br />– Soubory HTML.<br /><br /> Soubor prostředků obsahuje soubor Afxres.rc pro standardní prostředky aplikace Microsoft Foundation Class.|
|Resource.h|*Projname*|Soubory hlaviček|Hlavičkový soubor prostředků, který obsahuje definice pro prostředky používané tímto projektem.|
|*Název_projektu*.rc2|*Název_projektu*\res|Zdrojové soubory|Soubor skriptu obsahující další prostředky používané tímto projektem. Můžete zahrnout soubor .rc2 v souboru .rc v projektu.<br /><br /> Soubor s příponou .rc2 je užitečné pro zahrnutí prostředky využívané třídou několik různých projektech. Namísto toho, k vytvoření stejné prostředky pro různé projekty, můžete umístit je do souboru .rc2 a .rc2 soubor zahrnout do souboru .rc hlavní.|
|*Název_projektu*.def|*Projname*|Zdrojové soubory|Soubor definice modulu projektu knihovny DLL. Pro ovládací prvek obsahuje název a popis ovládacího prvku, a také velikost haldy za běhu.|
|*Název_projektu*.ico|*Název_projektu*\res|Zdrojové soubory|Soubor ikony na projekt nebo ovládací prvek. Tato ikona se zobrazuje, když je minimalizován aplikace. Používá se také v aplikačním **o** pole. Ve výchozím nastavení knihovna MFC poskytuje ikonu knihovny MFC a ATL obsahuje ikonu ATL.|
|*Název_projektu*Doc.ico|*Název_projektu*\res|Zdrojové soubory|Soubor ikony pro projekt knihovny MFC, včetně podpory pro architekturu document/view.|
|Toolbar.bmp s tím|*Název_projektu*\res|Zdrojové soubory|Soubor rastrového obrázku představující aplikace nebo ovládací prvek v panelu nástrojů nebo z palety. Tento rastrový obrázek je součástí souboru prostředků projektu. Počáteční nástrojů a stavový řádek jsou vytvořeny v **CMainFrame** třídy.|
|ribbon.mfcribbon-ms|*Název_projektu*\res|Zdrojové soubory|Soubor prostředků, která obsahuje kód XML, který definuje tlačítka, ovládací prvky a atributy pásu karet. Další informace najdete v tématu [Návrhář pásu karet (MFC)](../../mfc/ribbon-designer-mfc.md).|

## <a name="see-also"></a>Viz také:

[Soubor typy vytvořené pro sadu Visual Studio C++ projekty](file-types-created-for-visual-cpp-projects.md)
