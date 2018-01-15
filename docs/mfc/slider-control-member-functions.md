---
title: "Členské funkce ovládacího prvku posuvník | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CSliderCtrl class [MFC], methods
- slider controls [MFC], member functions
ms.assetid: dbde49ee-7306-4d14-a6ce-d09aa198178f
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1bd6c1d05ce7b137e6153ad2ea3fc5df99565a52
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="slider-control-member-functions"></a>Členské funkce ovládacího prvku jezdec
Aplikace může volat jezdec členské funkce ovládacího prvku k načtení informací o ovládacího prvku jezdec ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) a chcete-li změnit jeho vlastnosti.  
  
 Chcete-li načíst pozice posuvníku (to znamená, hodnota výběru uživatelem), použijte [GetPos](../mfc/reference/csliderctrl-class.md#getpos) – členská funkce. Pokud chcete nastavit pozice posuvníku, použijte [SetPos](../mfc/reference/csliderctrl-class.md#setpos) – členská funkce. Kdykoli můžete použít `VerifyPos` – členská funkce a ujistěte se, že posuvník je mezi minimální a maximální hodnoty.  
  
 Rozsah ovládací prvek typu jezdec je sada souvislý hodnoty, které může představovat posuvníku. Většina aplikací pomocí [setrange –](../mfc/reference/csliderctrl-class.md#setrange) – členská funkce a nastavte rozsah ovládací prvek typu jezdec, když je poprvé vytvořen. Aplikace můžete dynamicky upravit rozsah po vytvoření pomocí ovládacího prvku jezdec [SetRangeMax](../mfc/reference/csliderctrl-class.md#setrangemax) a [SetRangeMin](../mfc/reference/csliderctrl-class.md#setrangemin) členské funkce. Aplikace, která umožňuje oblast, kterou chcete změnit dynamicky obvykle načte nastavení poslední rozsah, když uživatel dokončí práci pomocí ovládacího prvku posuvník. Chcete-li načíst tato nastavení, použijte [getrange –](../mfc/reference/csliderctrl-class.md#getrange), [GetRangeMax](../mfc/reference/csliderctrl-class.md#getrangemax), a [GetRangeMin](../mfc/reference/csliderctrl-class.md#getrangemin) členské funkce.  
  
 Aplikace můžete použít `TBS_AUTOTICKS` styl tak, aby měl osové značky ovládacího prvku posuvník nezobrazí automaticky. Pokud aplikace potřebuje k řízení polohy nebo četnost značek, ale počet členské funkce můžete použít.  
  
 Pokud chcete nastavit pozici osových značek, můžete použít aplikaci [SetTic](../mfc/reference/csliderctrl-class.md#settic) – členská funkce. [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq) – členská funkce umožňuje aplikaci nastavit osové značky, které se zobrazují v pravidelných intervalech v prvku posuvník rozsahu. Například aplikace, můžete použít tuto funkci člen zobrazení značek jenom 10 v rozsahu od 1 do 100.  
  
 Chcete-li načíst index v rozsahu odpovídající osových značek, použijte [GetTic](../mfc/reference/csliderctrl-class.md#gettic) – členská funkce. [GetTicArray](../mfc/reference/csliderctrl-class.md#getticarray) – členská funkce načte pole tyto indexy. Pro načtení pozice osových značek v souřadnice klienta, použijte [GetTicPos](../mfc/reference/csliderctrl-class.md#getticpos) – členská funkce. Aplikace můžete načíst počet značek pomocí [GetNumTics](../mfc/reference/csliderctrl-class.md#getnumtics) – členská funkce.  
  
 [ClearTics](../mfc/reference/csliderctrl-class.md#cleartics) – členská funkce odebere všechny prvku posuvník osové značky.  
  
 Velikost řádku prvku posuvník Určuje, jak daleko posuvníku přesune, když obdrží aplikace **TB_LINEDOWN** nebo **TB_LINEUP** oznámení. Podobně je velikost stránky určuje odpověď na **TB_PAGEDOWN** a **TB_PAGEUP** zpráv s oznámením. Aplikace můžete načítat a nastavovat hodnoty velikosti řádku a stránku s použitím [GetLineSize](../mfc/reference/csliderctrl-class.md#getlinesize), [SetLineSize](../mfc/reference/csliderctrl-class.md#setlinesize), [GetPageSize](../mfc/reference/csliderctrl-class.md#getpagesize), a [SetPageSize](../mfc/reference/csliderctrl-class.md#setpagesize) členské funkce.  
  
 Aplikace můžete použít k načtení dimenze pro ovládací prvek typu jezdec členské funkce. [GetThumbRect](../mfc/reference/csliderctrl-class.md#getthumbrect) – členská funkce načte ohraničující obdélník pro posuvníku. [GetChannelRect](../mfc/reference/csliderctrl-class.md#getchannelrect) – členská funkce načte ohraničující obdélník pro ovládací prvek jezdec kanál. (Kanál je přes která přesune posuvník a obsahující zvýraznění při výběru rozsahu oblasti.)  
  
 Pokud má ovládací prvek typu jezdec `TBS_ENABLESELRANGE` styl, kterého uživatel může vybrat rozsah hodnot souvislý z něj. Počet členské funkce povolit výběr rozsahu upraví dynamicky. [SetSelection](../mfc/reference/csliderctrl-class.md#setselection) – členská funkce nastaví počáteční a koncová pozice výběru. Po dokončení nastavení výběru rozsahu uživatele aplikace můžete načíst nastavení pomocí [GetSelection](../mfc/reference/csliderctrl-class.md#getselection) – členská funkce. Chcete-li zrušte výběr uživatele, použijte [ClearSel](../mfc/reference/csliderctrl-class.md#clearsel) – členská funkce.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

