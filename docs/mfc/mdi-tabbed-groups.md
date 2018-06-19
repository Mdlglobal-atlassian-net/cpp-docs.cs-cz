---
title: MDI – skupiny se záložkami | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- mdi [MFC], tabbed groups
- tabbed grous [MFC]
ms.assetid: 0a464f36-39b7-4e68-8b67-ec175de28377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a7cf6420a331d46f2a158c16a30d439f334a46b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350351"
---
# <a name="mdi-tabbed-groups"></a>MDI – skupiny se záložkami
Více funkce skupiny v záložkách rozhraní (MDI) dokumentu umožňuje více aplikací rozhraní (MDI) dokumentu pro zobrazení jeden nebo více záložkách windows (nebo skupiny systému windows s kartami, označuje jako *– skupiny se záložkami*) v oblasti MDI klienta. Okna s kartami lze zarovnávat vodorovně nebo svisle. Pokud aplikace je hostitelem více než jedné skupině záložkách MDI, skupiny jsou odděleny příčky.  
  
## <a name="features"></a>Funkce  
 Následující části jsou uvedené funkce MDI – záložkami skupiny:  
  
-   Aplikace můžete vytvořit dynamicky záložkách windows.  
  
-   Aplikace můžete zarovnat záložkách windows vodorovně nebo svisle.  
  
-   Skupiny systému windows s kartami jsou odděleny příčky. Uživatel může změnit velikost skupiny v záložkách pomocí rozdělovače.  
  
-   Uživatele můžete přetáhnout jednotlivé karty mezi skupinami.  
  
-   Uživatele můžete přetáhnout jednotlivé karty k vytvoření nové skupiny.  
  
-   Uživatele můžete přesunout karty nebo vytvářet nové skupiny pomocí místní nabídky.  
  
-   Aplikace můžete uložit a načíst rozložení záložkách windows.  
  
-   Aplikace můžete uložit a načíst seznam MDI dokumentů.  
  
-   Aplikaci můžete získat přístup k jednotlivé skupiny v záložkách a upravit jejich parametrů.  
  
### <a name="using-mdi-tabbed-groups"></a>Pomocí MDI – skupiny se záložkami  
 Toto jsou úlohy běžně prováděné s MDI – záložkami skupiny:  
  
-   Chcete-li povolit MDI – záložkami skupiny pro okno rámce, volejte [CMDIFrameWndEx::EnableMDITabbedGroups](../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups). Druhý parametr této metody je instance `CMDITabInfo` třídy. Můžete použít výchozí parametry nebo je upravit před voláním `CMDIFrameWndEx::EnableMDITabbedGroups`.  
  
-   K úpravě vlastností skupiny záložkách MDI za běhu, vytvořit nebo upravit `CMDITabInfo` objekt a volání `CMDIFrameWndEx::EnableMDITabbedGroups` znovu  
  
-   Získat seznam MDI – záložkami windows, volání `CMDIFrameWndEx::GetMDITabGroups`.  
  
-   Chcete-li vytvořit novou skupinu s kartami MDI vedle skupiny služby active s kartami, volejte `CMDIFrameWndEx::MDITabNewGroup`.  
  
-   Chcete-li posunutí zaměření pro vstup na předchozí nebo další okno s kartami skupiny, volejte `CMDIFrameWndEx::MDITabMoveToNextGroup`.  
  
-   K určení, zda okno je členem skupiny MDI – volání skupiny se záložkami `CMDIFrameWndEx::IsMemberOfMDITabGroup`.  
  
-   Pokud chcete zjistit, zda MDI karty nebo MDI – záložkami skupiny jsou povoleny pro okno rámce, volání `CMDIFrameWndEx::AreMDITabs`. Pokud chcete zjistit, jestli jsou povolené MDI – záložkami skupiny, volání `CMDIFrameWndEx::IsMDITabbedGroup`.  
  
-   Chcete-li zobrazit místní nabídky, když uživatel klikne na kartě nebo nastavuje tažením ho do jiné skupiny s kartami MDI, přepište `CMDIFrameWndEx::OnShowMDITabContextMenu` v `CMDIFrameWndEx`-odvozené třídy. Pokud tato metoda neimplementují, nezobrazí aplikace místní nabídky.  
  
-   Chcete-li uložit rozložení MDI – záložkami skupin v aplikaci, volejte `CMDIFrameWndEx::SaveMDIState`. Načíst dříve uložené MDI – profil skupiny se záložkami, volejte `CMDIFrameWndEx::LoadMDIState`. Také můžete volat tyto metody pro načtení nebo uložení seznamu otevřených dokumentů v aplikaci MDI. Další informace o ukládání a načítání MDI stavu najdete v tématu [CMDIFrameWndEx::LoadMDIState](../mfc/reference/cmdiframewndex-class.md#loadmdistate).  
  
## <a name="see-also"></a>Viz také  
 [Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)   
 [CMDIFrameWndEx – třída](../mfc/reference/cmdiframewndex-class.md)   
 [CMDIChildWndEx – třída](../mfc/reference/cmdichildwndex-class.md)   
 [CMDITabInfo – třída](../mfc/reference/cmditabinfo-class.md)
