---
title: Nastavení pro třídu CStatusBarCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1dde1f005e53aff7ebe505d1ce619bf5c94410f8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955453"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Nastavení pro třídu CStatusBarCtrl
Výchozí umístění [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) okno Stav je podél dolního okraje nadřazeného okna, ale můžete určit styl CCS_TOP jej zobrazí v horní části okna nadřazené klientské oblasti.  
  
 Můžete určit styl SBARS_SIZEGRIP zahrnout úchyt na pravém konci `CStatusBarCtrl` okno stav. Úchyt je podobná velikosti ohraničení; je obdélníkovou oblast, která může uživatel klikněte a přetáhněte ke změně velikosti nadřazeného okna.  
  
> [!NOTE]
>  Pokud kombinujete styly CCS_TOP a SBARS_SIZEGRIP, výsledná úchyt není funkční, i když systém nevykresluje se v okně Stav.  
  
 Okno postup pro okno Stav automaticky nastaví počáteční velikost a umístění okna ovládacího prvku. Šířka je stejný jako u nadřazeného okna klientské oblasti. Výška je založena na metriky písma, které je aktuálně vybrané do kontextu okna Stav zařízení a na šířku ohraničení okna.  
  
 Postup okno automaticky upraví velikost okna stavu, vždy, když obdrží zprávu WM_SIZE. Obvykle když se změní velikost nadřazené okno, nadřazený odešle zprávu WM_SIZE do okna stav.  
  
 Můžete nastavit minimální výšku oblasti výkresu stavové okno voláním [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight), určení minimální výška v pixelech. Oblasti výkresu nezahrnuje okna ohraničení.  
  
 Načtení šířku ohraničení okno stav voláním [GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders). Tato funkce člen zahrnuje má ukazatel na tři element pole, které obdrží šířku ohraničení vodorovné, svislé ohraničení a ohraničení mezi obdélníky.  
  
## <a name="see-also"></a>Viz také  
 [Použití třídy CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

