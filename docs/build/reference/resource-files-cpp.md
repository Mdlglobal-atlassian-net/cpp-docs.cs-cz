---
title: Zdrojové soubory (C++)
ms.date: 05/14/2019
helpviewer_keywords:
- resource files
- resources [C++]
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
ms.openlocfilehash: 16759a242325b6a8e5f829f719ce3e505b03c2e3
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415849"
---
# <a name="resource-files-c"></a>Zdrojové soubory (C++)

Prostředky jsou prvky rozhraní, které uživateli poskytují informace. Rastrové obrázky, ikony, panely nástrojů a kurzory jsou všechny prostředky. Některé prostředky mohou provádět akce, jako je například výběr z nabídky nebo zadání dat do dialogového okna.

Další informace najdete v tématu [práce s prostředky](../../windows/working-with-resource-files.md).

|Název souboru|Umístění adresáře|Umístění Průzkumník řešení|Popis|
|---------------|------------------------|--------------------------------|-----------------|
|*ProjName*. RC|*Projname*|Zdrojové soubory|Soubor skriptu prostředků pro projekt. Soubor skriptu prostředků obsahuje následující, v závislosti na typu projektu, a podporu, která je vybrána pro projekt (například panely nástrojů, dialogová okna nebo HTML):<br /><br />– Výchozí definice nabídky<br />– Akcelerátor a tabulky řetězců.<br />– Dialogové **okno** s výchozím nastavením.<br />– Ostatní dialogová okna.<br />-Ikona souboru (res\\*ProjName*. ico).<br />– Informace o verzi.<br />Rastrové obrázky.<br />Pruhu.<br />– Soubory HTML.<br /><br /> Soubor prostředků obsahuje soubor AFXRES. RC pro standardní prostředky Microsoft Foundation Class.|
|Resource.h|*Projname*|Soubory hlaviček|Soubor hlaviček prostředků, který obsahuje definice pro prostředky používané projektem.|
|*ProjName*. RC2|*ProjName*\res|Zdrojové soubory|Soubor skriptu, který obsahuje další prostředky, které používá projekt. Do souboru. RC projektu můžete zahrnout soubor. RC2.<br /><br /> Soubor. RC2 je vhodný pro zahrnutí prostředků používaných několika různými projekty. Místo toho, abyste museli vytvářet stejné prostředky několikrát pro různé projekty, je můžete umístit do souboru. RC2 a zahrnout soubor. RC2 do hlavního souboru. rc.|
|*ProjName*. def|*Projname*|Zdrojové soubory|Soubor definice modulu pro projekt knihovny DLL. Pro ovládací prvek poskytuje název a popis ovládacího prvku a také velikost haldy běhu.|
|*ProjName*. ico|*ProjName*\res|Zdrojové soubory|Soubor ikony pro projekt nebo ovládací prvek. Tato ikona se zobrazí při minimalizaci aplikace. Používá se také v okně **o** aplikaci. Ve výchozím nastavení knihovna MFC poskytuje ikonu knihovny MFC a knihovna ATL poskytuje ikonu ATL.|
|*ProjName* Doc. ico|*ProjName*\res|Zdrojové soubory|Soubor ikony pro projekt knihovny MFC, který obsahuje podporu pro architekturu document/view.|
|Panel nástrojů. bmp|*ProjName*\res|Zdrojové soubory|Rastrový soubor, který představuje aplikaci nebo ovládací prvek na panelu nástrojů nebo v paletě. Tato bitmapa je obsažena v souboru prostředků projektu. Počáteční panel nástrojů a stavový řádek je vytvořen ve třídě **CMainFrame** .|
|pás karet. mfcribbon – ms|*ProjName*\res|Zdrojové soubory|Soubor prostředků, který obsahuje kód XML, který definuje tlačítka, ovládací prvky a atributy na pásu karet. Další informace najdete v tématu [Návrhář pásu karet (MFC)](../../mfc/ribbon-designer-mfc.md).|

## <a name="see-also"></a>Viz také

[Typy souborů vytvořených pro projekty sady C++ Visual Studio](file-types-created-for-visual-cpp-projects.md)
