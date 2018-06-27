---
title: Výběr položek ovládacího prvku strom | Microsoft Docs
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
ms.openlocfilehash: fc533046695db409067ff603e30cedbe11ad5ca4
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953554"
---
# <a name="tree-control-item-selection"></a>Výběr položek ovládacího prvku strom
Při výběru změní z jednu položku na jiný, ovládacím prvkem strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) odešle [TVN_SELCHANGING](http://msdn.microsoft.com/library/windows/desktop/bb773547) a [TVN_SELCHANGED](http://msdn.microsoft.com/library/windows/desktop/bb773544) zpráv s oznámením. Obě oznámení zahrnují hodnotu, která určuje, zda změna výsledku kliknutí myši nebo stisknutí klávesy. Oznámení také obsahují informace o položce, který je získání výběru a položku, je ztráty výběr. Tyto informace slouží k nastavení atributů položky, které závisí na stavu výběru položky. Vrácení **TRUE** v reakci na `TVN_SELCHANGING` brání výběr z změna; vrácení **FALSE** umožňuje změnu.  
  
 Aplikace můžete změnit výběr voláním [selectitem –](../mfc/reference/ctreectrl-class.md#selectitem) – členská funkce.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

