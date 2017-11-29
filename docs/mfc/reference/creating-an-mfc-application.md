---
title: "Vytváření aplikací MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: eb5f30dfaf3710e1b3dbe782a0aa24b3cd02deb4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-an-mfc-application"></a>Vytvoření aplikace MFC
Aplikace MFC je spustitelný soubor aplikace pro Windows, která je založena na knihovna Microsoft Foundation Class (MFC). Nejjednodušší způsob, jak vytvořit aplikaci MFC je použití Průvodce aplikací MFC.  
  
> [!IMPORTANT]
>  Projekty knihovny MFC nejsou podporovány v edicích sady Visual Studio Express.  
  
 Spustitelné soubory knihovny MFC obvykle spadají do pěti typů: standardní aplikace systému Windows, dialogová okna, formulářů, aplikace ve stylu Průzkumníku a webové prohlížeče stylu aplikace. Další informace naleznete v tématu:  
  
-   [Použití tříd pro psaní aplikací systému Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)  
  
-   [Vytváření a zobrazování dialogových oken](../../mfc/creating-and-displaying-dialog-boxes.md)  
  
-   [Vytváření aplikací MFC založených na formulářích](../../mfc/reference/creating-a-forms-based-mfc-application.md)  
  
-   [Vytváření aplikací MFC ve stylu Průzkumníka souborů](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)  
  
-   [Vytváření aplikací MFC webové prohlížeče – styl](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)  
  
 Průvodce aplikací MFC generuje příslušné třídy a soubory pro některý z těchto typů aplikací, v závislosti na možnostech, které vyberete v průvodci.  
  
### <a name="to-create-an-mfc-application-using-the-mfc-application-wizard"></a>K vytvoření aplikace knihovny MFC pomocí Průvodce aplikací MFC  
  
1.  Postupujte podle pokynů v tématu nápovědy [vytvoření projektu pomocí Průvodce aplikací Visual C++](../../ide/creating-desktop-projects-by-using-application-wizards.md).  
  
2.  V **nový projekt** dialogové okno, vyberte **aplikace knihovny MFC** v podokně šablon otevřete průvodce.  
  
3.  Zadejte nastavení aplikace pomocí [Průvodce aplikací knihovny MFC](../../mfc/reference/mfc-application-wizard.md).  
  
    > [!NOTE]
    >  Přeskočit tento krok průvodce zachovat výchozí nastavení.  
  
4.  Klikněte na tlačítko **Dokončit** zavřete průvodce a otevřete nový projekt ve vývojovém prostředí.  
  
 Po vytvoření projektu, můžete zobrazit soubory vytvořené v **Průzkumníku řešení**. Další informace o souborech Průvodce vytvoří pro váš projekt, naleznete v souboru projektu vygenerované souboru ReadMe.txt. Další informace o typech souborů najdete v tématu [typy souborů vytvořené pro projekty Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md).  
  
## <a name="see-also"></a>Viz také  
 [Příprava ladění: Aplikace Visual C++ Windows](http://msdn.microsoft.com/en-us/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5)   
 [Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Stránky vlastností](../../ide/property-pages-visual-cpp.md)   
 [Nasazení aplikací](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)
