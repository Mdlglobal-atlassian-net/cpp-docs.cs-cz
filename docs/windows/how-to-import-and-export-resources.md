---
title: "Postupy: Import a Export prostředků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.resvw.resource.importing
- vc.resvw.resource.importing
dev_langs: C++
helpviewer_keywords:
- resources [Visual Studio], exporting
- graphics [C++], exporting
- graphics [C++], importing
- resources [Visual Studio], importing
- bitmaps [C++], importing and exporting
- toolbars [C++], importing
- images [C++], importing
- toolbars [C++], exporting
- cursors [C++], importing and exporting
- images [C++], exporting
ms.assetid: 3c9329dc-dcb8-4edd-a600-78e3e572bd89
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 21f596996d090d9d41146c6f8ea9cb24884dd4c0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-import-and-export-resources"></a>Postupy: Import a export prostředků
Můžete importovat grafických prostředků (rastrové obrázky, ikonami, kurzory a panely nástrojů), soubory HTML a vlastní prostředky pro použití v jazyce Visual C++. Stejné typy souborů, můžete exportovat z projektu Visual C++ do samostatných souborů, které lze použít mimo vývojového prostředí.  
  
> [!NOTE]
>  Typy prostředků, jako je například řetězec tabulek akcelerátorů, dialogová okna a nelze importovat nebo exportovat, protože nejsou typy samostatné souborů.  
  
### <a name="to-import-an-individual-resource-into-your-current-resource-file"></a>K importu jednotlivých prostředků do aktuální soubor prostředků  
  
1.  V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na uzel pro skript prostředků (* .rc) souboru, do které chcete přidat prostředek.  
  
2.  Klikněte na tlačítko **Import** v místní nabídce.  
  
3.  Vyhledejte a vyberte název souboru rastrový obrázek (BMP), ikona (), kurzor (), soubor Html (*.htm) nebo jiný soubor, který chcete importovat.  
  
4.  Klikněte na tlačítko **OK** pro daný prostředek přidejte do vybraného souboru v **prostředků** zobrazení.  
  
    > [!NOTE]
    >  Proces importu funguje stejným způsobem, bez ohledu na to, který prostředek se konkrétní typ vybrali. Importovaných zdrojů je automaticky přidán do správný uzel pro tento typ prostředku.  
  
### <a name="to-export-a-bitmap-icon-or-cursor-as-a-separate-file-for-use-outside-of-visual-c"></a>Chcete-li exportovat rastrového obrázku, ikony nebo kurzoru jako samostatný soubor (za účelem použití mimo Visual C++)  
  
1.  V **prostředků** zobrazit, klikněte pravým tlačítkem na prostředek, který chcete exportovat.  
  
2.  Klikněte na tlačítko **exportovat** v místní nabídce.  
  
3.  V **Export prostředků** dialogové okno pole, přijměte aktuální název nebo zadejte nový.  
  
4.  Přejděte do složky, kam chcete uložit soubor a klikněte na tlačítko **exportovat**.  
  

  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Soubory prostředků](../windows/resource-files-visual-studio.md)   
 [Editory prostředků](../windows/resource-editors.md)