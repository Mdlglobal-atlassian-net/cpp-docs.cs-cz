---
title: "Implementace stavového řádku v prostředí MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: COldStatusBar
dev_langs: C++
helpviewer_keywords:
- status bars [MFC], implementing in MFC
- CStatusBarCtrl class [MFC], and MFC status bars
- CStatusBar class [MFC], and CStatusBarCtrl class [MFC]
- CStatusBarCtrl class [MFC], and CStatusBar class [MFC]
- status bars [MFC], backward compatibility
- status bars [MFC], old with COldStatusBar class [MFC]
- COldStatusBar class [MFC]
- status bars [MFC], and CStatusBarCtrl class
- CStatusBar class [MFC], and MFC status bars
- status indicators
- status bars [MFC], Windows 95 implementation
ms.assetid: be5cd876-38e3-4d5c-b8cb-16d57a16a142
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ad340de74193bedbe817f1cd5bb5cc29b3417195
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="status-bar-implementation-in-mfc"></a>Implementace stavového řádku v prostředí MFC
A [cstatusbar –](../mfc/reference/cstatusbar-class.md) objekt je ovládací prvek panel s řádek podokna výstup textu. Podokna výstup běžně se používají jako řádky zprávy a jako indikátory stavu. Mezi příklady patří řádky zprávu nápovědy nabídky, které stručně popisují příkaz vybrané nabídky a indikátory, které se zobrazí stav SCROLL LOCK NUMLOCK a jiných klíčů.  
  
 Od verze knihovny MFC verze 4.0, stavové řádky jsou implementované pomocí třídy [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md), který zapouzdří stav panelu běžného ovládacího prvku. Z důvodu zpětné kompatibility MFC uchovává starší implementace řádku stav v třídě **COldStatusBar**. Dokumentace pro starší verze knihovny MFC popisuje **COldStatusBar** pod `CStatusBar`.  
  
 [CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl), členské funkce nové MFC 4.0, můžete využít podporu Windows běžné ovládacího prvku pro stavovém řádku přizpůsobení a další funkce. `CStatusBar`Členské funkce získáte většinu funkcí běžných ovládacích prvků Windows; ale při volání `GetStatusBarCtrl`, můžete udělit stavové řádky i více společných vlastností stavového řádku. Při volání `GetStatusBarCtrl`, vrátí odkaz na `CStatusBarCtrl` objektu. Tento odkaz můžete použít k manipulaci s ovládacího prvku panel stav.  
  
 Následující obrázek znázorňuje stavový řádek, který zobrazí několik ukazatele.  
  
 ![Stavový řádek](../mfc/media/vc37dy1.gif "vc37dy1")  
Stavový řádek  
  
 Jako panelu nástrojů objekt stavového řádku vložené do jeho nadřazeného rámce okna a je automaticky vytvořen, když se okně s rámečkem. Stavový řádek, jako jsou všechny ovládací pruhy automaticky zničen také při nadřazeného rámce zničena.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Aktualizace textu panelu Stav řádku](../mfc/updating-the-text-of-a-status-bar-pane.md)  
  
-   MFC – třídy [cstatusbar –](../mfc/reference/cstatusbar-class.md) a [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
  
-   [Ovládací pruhy](../mfc/control-bars.md)  
  
-   [Dialogové pruhy](../mfc/dialog-bars.md)  
  
-   [Panely nástrojů (MFC – implementace panelu nástrojů)](../mfc/mfc-toolbar-implementation.md)  
  
## <a name="see-also"></a>Viz také  
 [Stavové řádky](../mfc/status-bars.md)

