---
title: "Soubory prostředků (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- resource files
- resources [C++]
- file types [C++], resource files
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 097ae6d1486292d7dcc62dd4191e16f57e6f0a3c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="resource-files-c"></a>Zdrojové soubory (C++)
Prostředky jsou elementy rozhraní, které obsahují informace pro uživatele. Rastrové obrázky, ikonami, panely nástrojů a kurzory jsou všechny prostředky. Některé prostředky, se dá provést akce, jako z nabídky Výběr nebo zadávání dat v dialogovém okně Upravit.  
  
 V tématu [práci s prostředky](../windows/working-with-resource-files.md) Další informace.  
  
|Název souboru|Umístění adresáře|Umístění v Průzkumníku řešení|Popis|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Projname*.rc|*Projname*|Zdrojové soubory|Souboru skriptu prostředků pro projekt. Souboru skriptu prostředků obsahuje následující příkaz, v závislosti na typu projektu a vybrané podpory pro projekt (například panely nástrojů, dialogová okna nebo HTML):<br /><br /> -Výchozí definici nabídky.<br />-Tabulky akcelerátoru a řetězec.<br />-Výchozí **o** dialogové okno.<br />-Další dialogová okna.<br />-Soubor ikony (res\\*Projname*.ico).<br />-Informace o verzi.<br />-Rastrové obrázky.<br />-Panelu nástrojů.<br />– Soubory HTML.<br /><br /> Soubor prostředků obsahuje soubor Afxres.rc pro standardní prostředky aplikace Microsoft Foundation Class.|  
|Resource.h|*Projname*|Soubory hlaviček|Soubor hlaviček prostředku, který obsahuje definice pro prostředky používané projektu.|  
|*Projname*.rc2|*Projname*\res|Zdrojové soubory|Souboru skriptu, který obsahuje další prostředky využívané třídou projektu. Můžete zahrnout soubor .rc2 v horní části souboru .rc projektu.<br /><br /> Soubor .rc2 je užitečné pro včetně prostředků používá několik různých projektů. Místo nutnosti vytvořit stejné prostředky pro různé projekty, můžete je uložit soubor .rc2 a zahrnout soubor .rc2 do hlavní soubor.|  
|*Projname*.def|*Projname*|Zdrojové soubory|Soubor definice modulu pro projektu knihovny DLL. Pro ovládací prvek poskytuje název a popis ovládacího prvku, a také velikost haldy běhu.|  
|*Projname*.ico, který|*Projname*\res|Zdrojové soubory|Soubor ikony pro projekt nebo ovládací prvek. Tato ikona se zobrazí, když je minimalizován aplikace. Používá se také do aplikace **o** pole. Ve výchozím nastavení MFC obsahuje ikonu MFC a knihovny ATL poskytuje ikonu ATL.|  
|*Projname*Doc.ico|*Projname*\res|Zdrojové soubory|Soubor ikony pro projekt knihovny MFC, který zahrnuje podporu pro architektuře dokument/zobrazení.|  
|Toolbar.bmp s tím|*Projname*\res|Zdrojové soubory|Rastrového obrázku představující aplikace nebo ovládací prvek v panelu nástrojů nebo palety. Tento rastrový obrázek je součástí souboru prostředků projektu. Počáteční panel nástrojů a stavového řádku v zkonstruovat **CMainFrame** třídy.|  
|Ribbon.mfcribbon-ms|*Projname*\res|Zdrojové soubory|Soubor prostředků, který obsahuje kód XML, který definuje tlačítka, ovládací prvky a atributy na pásu karet. Další informace najdete v tématu [Návrhář pásu karet (MFC)](../mfc/ribbon-designer-mfc.md).|  
  
## <a name="see-also"></a>Viz také  
 [Typy souborů vytvořených pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)