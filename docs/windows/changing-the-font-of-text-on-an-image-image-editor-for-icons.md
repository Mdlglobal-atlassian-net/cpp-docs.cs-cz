---
title: "Změna písma textu obrázku (Editor obrázků pro ikony) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: fonts, changing on an image
ms.assetid: b8849d40-d401-4e06-808f-e615cb2bee3b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 86942af0085bf749c8e1bbbab27a9a674164da79
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="changing-the-font-of-text-on-an-image-image-editor-for-icons"></a>Změna písma textu obrázku (editor obrázků pro ikony)
Následující postup je příklad toho, jak:  
  
-   Přidat text na ikonu v aplikaci Windows  
  
-   Manipulace s písmo textu  
  
### <a name="to-change-the-font-of-text-on-an-image"></a>Změna písma textu obrázku  
  
1.  Vytvoření Formulářové aplikace C++ Windows. Podrobnosti najdete v tématu [vytváření projekt aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa). [Šablona Formulářové aplikace Windows](http://msdn.microsoft.com/en-us/1babdebf-ab3f-4a64-a608-98499a5b9cea) přidá soubor s názvem app.ico do projektu ve výchozím nastavení.  
  
2.  V Průzkumníku řešení poklikejte na soubor app.ico. [Editor obrázků](../windows/image-editor-for-icons.md) se otevře.  
  
3.  Z **Image** nabídce vyberte možnost **nástroje** a pak vyberte **textový nástroj**. [Dialogové okno textový nástroj](../windows/text-tool-dialog-box-image-editor-for-icons.md) se zobrazí.  
  
4.  V dialogovém okně Nástroj Text zadejte `C++` v oblasti prázdný text. Tento text se zobrazí s možností změny velikosti pole umístěné v levém horním rohu app.ico, v editoru obrázků.  
  
5.  V editoru obrázků, přetáhněte pole s možností změny velikosti k centru app.ico ke zlepšení čitelnosti textu.  
  
6.  V dialogovém okně Nástroj Text, klikněte na **písma** tlačítko. [Dialogové okno písmo textového nástroje](../windows/text-tool-font-dialog-box-image-editor-for-icons.md) se zobrazí.  
  
7.  V dialogovém okně textový nástroj písma vyberte **Times New Roman** ze seznamu dostupných písem, které jsou uvedeny v **písma** pole se seznamem.  
  
8.  Vyberte **Bold** ze seznamu uvedené v styly dostupné písmo **styl písma** pole se seznamem.  
  
9. Vyberte **10** ze seznamu dostupných velikosti uvedené v bodu **velikost** pole se seznamem.  
  
10. Klikněte **OK** tlačítko. Dialogové okno textový nástroj písmo se zavře a uplatní se nové nastavení písma v textu.  
  
11. Klikněte **Zavřít** tlačítka v dialogovém okně nástroje Text. Pole s možností změny velikosti kolem text zmizí z editoru bitové kopie.  
  
## <a name="see-also"></a>Viz také  
 [Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Panel nástrojů](../windows/toolbar-image-editor-for-icons.md)

