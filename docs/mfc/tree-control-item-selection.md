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
ms.openlocfilehash: 6fb08fcbb1bd77cc80fdbe014d8c9e8a0851254d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385895"
---
# <a name="tree-control-item-selection"></a>Výběr položek ovládacího prvku strom
Při výběru změní z jednu položku na jiný, ovládacím prvkem strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) odešle [TVN_SELCHANGING](http://msdn.microsoft.com/library/windows/desktop/bb773547) a [TVN_SELCHANGED](http://msdn.microsoft.com/library/windows/desktop/bb773544) zpráv s oznámením. Obě oznámení zahrnují hodnotu, která určuje, zda změna výsledku kliknutí myši nebo stisknutí klávesy. Oznámení také obsahují informace o položce, který je získání výběru a položku, je ztráty výběr. Tyto informace slouží k nastavení atributů položky, které závisí na stavu výběru položky. Vrácení **TRUE** v reakci na **TVN_SELCHANGING** brání výběr z změna; vrácení **FALSE** umožňuje změnu.  
  
 Aplikace můžete změnit výběr voláním [selectitem –](../mfc/reference/ctreectrl-class.md#selectitem) – členská funkce.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

