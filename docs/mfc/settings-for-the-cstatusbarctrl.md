---
title: "Nastavení pro třídu CStatusBarCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CStatusBarCtrl
dev_langs: C++
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 814c12b13333d589cb568c5c637f0fa34956847e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="settings-for-the-cstatusbarctrl"></a>Nastavení pro třídu CStatusBarCtrl
Výchozí umístění [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) okno Stav je podél dolního okraje nadřazeného okna, ale můžete zadat `CCS_TOP` styl, který se následně zobrazí v horní části okna nadřazené klientské oblasti.  
  
 Můžete zadat **SBARS_SIZEGRIP** styl zahrnout úchyt na pravém konci `CStatusBarCtrl` okno stav. Úchyt je podobná velikosti ohraničení; je obdélníkovou oblast, která může uživatel klikněte a přetáhněte ke změně velikosti nadřazeného okna.  
  
> [!NOTE]
>  Pokud kombinujete `CCS_TOP` a **SBARS_SIZEGRIP** styly, výsledná úchyt pro změnu velikosti nebude funkční, i když systém nevykresluje se v okně Stav.  
  
 Okno postup pro okno Stav automaticky nastaví počáteční velikost a umístění okna ovládacího prvku. Šířka je stejný jako u nadřazeného okna klientské oblasti. Výška je založena na metriky písma, které je aktuálně vybrané do kontextu okna Stav zařízení a na šířku ohraničení okna.  
  
 Postup okno automaticky upraví velikost okna stavu, vždy, když obdrží `WM_SIZE` zprávy. Obvykle, když velikost nadřazené okno změní, odešle nadřazená `WM_SIZE` zprávu, která se stavové okno.  
  
 Můžete nastavit minimální výšku oblasti výkresu stavové okno voláním [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight), určení minimální výška v pixelech. Oblasti výkresu nezahrnuje okna ohraničení.  
  
 Načtení šířku ohraničení okno stav voláním [GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders). Tato funkce člen zahrnuje má ukazatel na tři element pole, které obdrží šířku ohraničení vodorovné, svislé ohraničení a ohraničení mezi obdélníky.  
  
## <a name="see-also"></a>Viz také  
 [Použití třídy CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

