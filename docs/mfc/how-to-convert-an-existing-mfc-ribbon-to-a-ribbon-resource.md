---
title: "Postupy: převod existujícího pásu karet MFC na prostředek pásu karet | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ribbon resource, converting from an MFC ribbon
- MFC ribbon, converting to a ribbon resource
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 97097618ee3f166866daad68190b7c22cca3c16d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource"></a>Postupy: Převod existujícího pásu karet MFC na prostředek pásu karet
Pás karet prostředky jsou usnadňují vizualizaci, úpravě a udržovat než ručně programové pásů karet. Toto téma popisuje, jak převést ručně programové pásu karet v projektu knihovny MFC na prostředek pásu karet.  
  
 Musí mít existující MFC projekt, který má kód, který používá třídy pásu karet MFC, například [CMFCRibbonBar Class](../mfc/reference/cmfcribbonbar-class.md).  
  
### <a name="to-convert-an-mfc-ribbon-to-a-ribbon-resource"></a>Převést pásu karet MFC na prostředek pásu karet  
  
1.  V sadě Visual Studio v existujícím projektu knihovny MFC otevření zdrojového souboru, kde je objekt CMFCRibbonBar inicializovat. Soubor je obvykle mainfrm.cpp. Přidejte následující kód po inicializaci kódu pro pás karet.  
  
 ```  
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");

 ```  
  
     Soubor uložte a zavřete.  
  
2.  Sestavení a spuštění aplikace MFC v poznámkovém bloku otevřete RibbonOutput.txt a zkopírujte její obsah.  
  
3.  V sadě Visual Studio na **projektu** nabídky, klikněte na tlačítko **přidat prostředek**. V **přidat prostředek** dialogové okno, vyberte **pásu karet** a pak klikněte na **nový**.  
  
     Visual Studio vytvoří prostředek pásu karet a otevře ji v zobrazení návrhu. ID prostředku pásu karet je IDR_RIBBON1, který se zobrazí v **zobrazení prostředků**. Na pásu karet je definována v souboru XML ribbon1.mfcribbon ms.  
  
4.  V sadě Visual Studio otevřete ribbon1.mfcribbon-ms, odstranit její obsah a vložte obsah RibbonOutput.txt, který jste zkopírovali dříve. Uložte a zavřete ribbon1.mfcribbon ms.  
  
5.  Znovu otevřít zdrojový soubor, kde je inicializovat objekt CMFCRibbonBar (obvykle mainfrm.cpp) a Odkomentujte existující kód pásu karet. Přidejte následující kód za kód, který je označeno jako komentář.  
  
 ```  
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);

 ```  
  
6.  Sestavte projekt a spusťte program.  
  
## <a name="see-also"></a>Viz také  
 [Návrhář pásu karet (MFC)](../mfc/ribbon-designer-mfc.md)
