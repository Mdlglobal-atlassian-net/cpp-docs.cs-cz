---
title: "Štítků ovládacích prvků strom úpravy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- editing tree control labels
- CTreeCtrl class [MFC], editing labels
- label editing in CTreeCtrl class [MFC]
- tree controls [MFC], label editing
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 03fb11c29b51b30b1aaffccbe3e999f1cefc3fbb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-label-editing"></a>Úpravy štítků ovládacích prvků strom
Uživatele můžete upravit přímo popisky položek v ovládacím prvku strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) má **TVS_EDITLABELS** stylu. Uživatel začne úpravy klepnutím na popisek položky, který je aktivní. Aplikace začne úpravy pomocí [EditLabel](../mfc/reference/ctreectrl-class.md#editlabel) – členská funkce. Ovládací prvek stromu odešle oznámení při úpravě začne a kdy je zrušena nebo byla dokončena. Po dokončení úprav jste zodpovědní za aktualizace popisek položky, podle potřeby.  
  
 Když úpravy štítků začne, odešle ovládacím prvkem strom [TVN_BEGINLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773506) oznámení. Zpracováním toto oznámení, můžete povolit úpravy některé popisků a zamezení úprav ostatní. Vrácení 0 umožňuje úpravy, a vrátí nenulovou nebude.  
  
 Když úpravy štítků je zrušena nebo byla dokončena, odešle ovládacím prvkem strom [TVN_ENDLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773515) oznámení. `lParam` Parametr je adresa [NMTVDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773418) struktury. **Položky** člen [TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) struktura označuje položku, která obsahuje upravený text. Jste zodpovědní za aktualizaci popisek položky v případě potřeby však možná po ověření upravená řetězec. **PszText** členem `TV_ITEM` je 0, pokud úpravy je zrušeno.  
  
 Během úpravy štítků, obvykle v reakci [TVN_BEGINLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773506) oznámení, můžete získat ukazatel do ovládacího prvku úprav používá pro úpravy štítků pomocí [GetEditControl](../mfc/reference/ctreectrl-class.md#geteditcontrol) člena funkce. Textové pole můžete volat [SetLimitText](../mfc/reference/cedit-class.md#setlimittext) – členská funkce a omezit tak velikost může uživatel zadat text nebo podtřídy ovládacího prvku úprav zachytí a zahodit neplatné znaky. Upozorňujeme však, že textové pole se zobrazí pouze *po* **TVN_BEGINLABELEDIT** se odesílají.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

