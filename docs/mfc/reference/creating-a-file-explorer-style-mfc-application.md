---
title: "Vytváření aplikací MFC ve stylu Průzkumníka souborů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfcexplorer.project
dev_langs: C++
helpviewer_keywords:
- browsers [MFC], Explorer-style applications
- MFC applications [MFC], Windows Explorer-style
- Explorer-style applications [MFC], creating
ms.assetid: f843ab5d-2d5d-41ca-88a4-badc0d2f8052
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e8e97253f74365ef0b3c3a235257c85ceee37b3f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-a-file-explorer-style-mfc-application"></a>Vytvoření aplikace knihovny MFC ve stylu Průzkumníka souborů
Mnoho aplikací systému Windows pomocí uživatelského rozhraní (UI) pro Průzkumníka souborů. Když spustíte Průzkumníka souborů, například zobrazí aplikace s svislé rozdělovače panelu dělení klientské oblasti. Na levé straně klientské oblasti poskytuje navigaci a procházení funkcí a na pravé straně klientské oblasti zobrazuje podrobnosti týkající se výběru v levém podokně. Když uživatel klikne na položku v levém podokně, aplikace znovu naplní v pravém podokně. V aplikaci MDI, můžete použít příkazy na **zobrazení** chcete změnit úroveň podrobností zobrazí v pravém podokně, v nabídce. (V aplikaci SDI nebo více dokumentů nejvyšší úrovně, můžete změnit podrobnosti, pomocí tlačítka panelu nástrojů.)  
  
 Obsah podoken závisí na aplikaci. V prohlížeči systému souborů v levém podokně zobrazuje hierarchické zobrazení adresáře nebo počítače nebo skupiny počítačů, zatímco v pravém podokně se zobrazí složky, jednotlivé soubory, nebo počítače a podrobnosti o nich. Obsah nemusí nutně být soubory. Může být e-mailových zpráv, zpráv o chybách nebo jiných položek v databázi.  
  
 Průvodce pro vás vytvoří následující třídy:  
  
-   **CLeftView** třída definuje v levém podokně klientské oblasti. Vždy je odvozený od [CTreeView](../../mfc/reference/ctreeview-class.md).  
  
-   C*ProjName*zobrazení třída definuje v pravém podokně klientské oblasti. Ve výchozím nastavení je odvozený od [CListView](../../mfc/reference/clistview-class.md) , ale může být jiný typ zobrazení v závislosti na třídě zadáte z **základní třída** v seznamu [generované třídy](../../mfc/reference/generated-classes-mfc-application-wizard.md) stránky Průvodce.  
  
 Vygenerovaný aplikace může mít jedním dokumentem (SDI rozhraní), rozhraní více dokumentů (MDI) nebo architekturu s více dokumenty nejvyšší úrovně. Aplikace vytvoří každý oken s rámečkem je svisle rozdělení pomocí [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md). Kódování tento typ aplikace je podobný kódování normální aplikace MFC, která používá oddělovače, s tím rozdílem, že tento typ aplikace má samostatné zobrazení ovládacích prvků v každém podokně oddělovače.  
  
 Pokud používáte výchozí zobrazení seznamu v pravém podokně, Průvodce vytvoří další nabídku možností (v pouze aplikace MDI) a tlačítka panelu nástrojů, chcete-li přepnout zobrazení stylu mezi ikony. velké ikony, ikony. Malé ikony, seznamu a podrobností režimy.  
  
### <a name="to-begin-creating-a-file-explorer-style-mfc-executable"></a>Zahajte proces vytváření spustitelný soubor MFC souboru stylu Průzkumníku  
  
1.  Postupujte podle pokynů v [vytváření aplikací MFC](../../mfc/reference/creating-an-mfc-application.md).  
  
2.  V Průvodce aplikací MFC [typ aplikace](../../mfc/reference/application-type-mfc-application-wizard.md) vyberte **Průzkumníka souborů** projektu stylu.  
  
3.  Nastavte další možnosti, které požadavky na dalších stránkách průvodce.  
  
4.  Klikněte na tlačítko **Dokončit** pro vygenerování kostru aplikace.  
  
 Další informace naleznete v tématu:  
  
-   [Více typů dokumentů, zobrazení a oken s rámečkem](../../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [Odvozené třídy zobrazení](../../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [Volby při návrhu aplikací](../../mfc/application-design-choices.md)  
  
## <a name="see-also"></a>Viz také  
 [MFC – Průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)   
 [Vytváření aplikací MFC webové prohlížeče – styl](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)   
 [Vytváření aplikací MFC založených na formulářích](../../mfc/reference/creating-a-forms-based-mfc-application.md)

