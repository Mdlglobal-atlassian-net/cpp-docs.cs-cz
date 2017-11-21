---
title: "Výběr položek ovládacího prvku strom | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fac551ed757cf0510f0a8b61522bc969c6b6be6d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="tree-control-item-selection"></a>Výběr položek ovládacího prvku strom
Při výběru změní z jednu položku na jiný, ovládacím prvkem strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) odešle [TVN_SELCHANGING](http://msdn.microsoft.com/library/windows/desktop/bb773547) a [TVN_SELCHANGED](http://msdn.microsoft.com/library/windows/desktop/bb773544) zpráv s oznámením. Obě oznámení zahrnují hodnotu, která určuje, zda změna výsledku kliknutí myši nebo stisknutí klávesy. Oznámení také obsahují informace o položce, který je získání výběru a položku, je ztráty výběr. Tyto informace slouží k nastavení atributů položky, které závisí na stavu výběru položky. Vrácení **TRUE** v reakci na **TVN_SELCHANGING** brání výběr z změna; vrácení **FALSE** umožňuje změnu.  
  
 Aplikace můžete změnit výběr voláním [selectitem –](../mfc/reference/ctreectrl-class.md#selectitem) – členská funkce.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

