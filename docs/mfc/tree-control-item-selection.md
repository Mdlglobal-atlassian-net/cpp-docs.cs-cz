---
title: Výběr položek ovládacího prvku strom | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd6632a44dd4806b8f13683b50cad76b5eebe27a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212578"
---
# <a name="tree-control-item-selection"></a>Výběr položek ovládacího prvku strom
Při změně výběru z jedné položky na jiný, ovládací prvek stromu ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) odešle [TVN_SELCHANGING](/windows/desktop/Controls/tvn-selchanging) a [TVN_SELCHANGED](/windows/desktop/Controls/tvn-selchanged) zpráv s oznámením. Obě oznámení zahrnují hodnotu, která určuje, zda změna je výsledkem kliknutí myší nebo stisknutí klávesy. Oznámení také zahrnovat informace o položce, která získává na výběr a položku, která je ztráta výběr. Tyto informace slouží k nastavení atributů položky, které závisí na stavu výběru položky. Vrací **TRUE** v reakci na `TVN_SELCHANGING` brání výběr změny; vrácení **FALSE** umožňuje změnu.  
  
 Aplikace můžete změnit výběr voláním [selectitem –](../mfc/reference/ctreectrl-class.md#selectitem) členskou funkci.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

