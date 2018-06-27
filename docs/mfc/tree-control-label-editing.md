---
title: Štítků ovládacích prvků strom úpravy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- editing tree control labels
- CTreeCtrl class [MFC], editing labels
- label editing in CTreeCtrl class [MFC]
- tree controls [MFC], label editing
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d665ae37bfc843fc2ab0f24fe4489b76935e62d2
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956262"
---
# <a name="tree-control-label-editing"></a>Úpravy štítků ovládacích prvků strom
Uživatele můžete upravit přímo popisky položek v ovládacím prvku strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) má **TVS_EDITLABELS** stylu. Uživatel začne úpravy klepnutím na popisek položky, který je aktivní. Aplikace začne úpravy pomocí [EditLabel](../mfc/reference/ctreectrl-class.md#editlabel) – členská funkce. Ovládací prvek stromu odešle oznámení při úpravě začne a kdy je zrušena nebo byla dokončena. Po dokončení úprav jste zodpovědní za aktualizace popisek položky, podle potřeby.  
  
 Když úpravy štítků začne, odešle ovládacím prvkem strom [TVN_BEGINLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773506) oznámení. Zpracováním toto oznámení, můžete povolit úpravy některé popisků a zamezení úprav ostatní. Vrácení 0 umožňuje úpravy, a vrátí nenulovou nebude.  
  
 Když úpravy štítků je zrušena nebo byla dokončena, odešle ovládacím prvkem strom [TVN_ENDLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773515) oznámení. *LParam* parametr je adresa [NMTVDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773418) struktury. **Položky** člen [TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) struktura označuje položku, která obsahuje upravený text. Jste zodpovědní za aktualizaci popisek položky v případě potřeby však možná po ověření upravená řetězec. *PszText* členem `TV_ITEM` je 0, pokud úpravy je zrušeno.  
  
 Během úpravy štítků, obvykle v reakci [TVN_BEGINLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773506) oznámení, můžete získat ukazatel do ovládacího prvku úprav používá pro úpravy štítků pomocí [GetEditControl](../mfc/reference/ctreectrl-class.md#geteditcontrol) člena funkce. Textové pole můžete volat [SetLimitText](../mfc/reference/cedit-class.md#setlimittext) – členská funkce a omezit tak velikost může uživatel zadat text nebo podtřídy ovládacího prvku úprav zachytí a zahodit neplatné znaky. Upozorňujeme však, že textové pole se zobrazí pouze *po* **TVN_BEGINLABELEDIT** se odesílají.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

