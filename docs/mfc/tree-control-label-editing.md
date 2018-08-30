---
title: Štítků ovládacích prvků strom úpravy | Dokumentace Microsoftu
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
ms.openlocfilehash: 7f9ba5360ddce81061bf73839e1700fed57c9fa7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210400"
---
# <a name="tree-control-label-editing"></a>Úpravy štítků ovládacích prvků strom
Uživatel může upravovat přímo popisky položek ovládacího prvku stromu ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)), který má **TVS_EDITLABELS** style. Uživatel začne upravovat po kliknutí popisek položky, která má fokus. Aplikace se začne upravovat pomocí [EditLabel](../mfc/reference/ctreectrl-class.md#editlabel) členskou funkci. Ovládací prvek stromu odesílá oznámení při úpravě začíná a kdy je zrušen nebo dokončení. Když po dokončení úprav, zodpovídáte za aktualizuje popisek položky v případě potřeby.  
  
 Úpravy štítků zahájení, odesílá se ovládacím prvkem strom [TVN_BEGINLABELEDIT](/windows/desktop/Controls/tvn-beginlabeledit) zprávy oznámení. Zpracováním toto oznámení, můžete povolit úpravu některé popisky a úpravami ostatních. Vrátí 0 umožňuje úpravy a vrací nenulovou hodnotu vypne.  
  
 Při úpravách popisek je zrušena nebo dokončeno, odešle ovládacím prvkem strom [TVN_ENDLABELEDIT](/windows/desktop/Controls/tvn-endlabeledit) zprávy oznámení. *LParam* parametr je adresa [NMTVDISPINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtvdispinfoa) struktury. **Položky** člen je [TVITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtvitema) struktura, která identifikuje položku a zahrnuje upraveného textu. Zodpovídáte za aktualizuje popisek položky v případě potřeby se možná po ověření upravený řetězec. *PszText* člen `TV_ITEM` je 0, pokud se zruší úpravy.  
  
 Během úpravy štítků, obvykle v reakci [TVN_BEGINLABELEDIT](/windows/desktop/Controls/tvn-beginlabeledit) zpráva s oznámením, můžete získat ukazatel na textové pole pro úpravy štítků s použitím [GetEditControl](../mfc/reference/ctreectrl-class.md#geteditcontrol) člena funkce. Můžete volat textovém poli [SetLimitText](../mfc/reference/cedit-class.md#setlimittext) členské funkce a omezit tak množství může uživatel zadat text nebo podtřídy ovládacího prvku pro úpravy a zachytit a zahodit neplatné znaky. Upozorňujeme, že ovládací prvek pro úpravy se zobrazí pouze *po* **TVN_BEGINLABELEDIT** se odesílají.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

