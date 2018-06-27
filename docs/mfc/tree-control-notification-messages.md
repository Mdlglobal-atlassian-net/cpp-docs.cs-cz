---
title: Zprávy s oznámením ovládacího prvku strom | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], tree controls
- messages [MFC], notification
- CTreeCtrl class [MFC], notifications
- notifications [MFC], CTreeCtrl
- tree controls [MFC], notification messages
ms.assetid: ac7013b4-91dd-4668-bd75-439ca0680ef9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 92035d3f1a20a0fd9cc0c7b95d7238ef014033da
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950964"
---
# <a name="tree-control-notification-messages"></a>Zprávy s oznámením ovládacího prvku strom
Ovládacím prvkem strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) odešle tyto zprávy s oznámením jako wm_notify – zprávy:  
  
|Zpráva upozornění|Popis|  
|--------------------------|-----------------|  
|TVN_BEGINDRAG|Signály spuštění operací přetažení myší|  
|TVN_BEGINLABELEDIT|Signály začátek úpravy štítků na místě|  
|TVN_BEGINRDRAG|Signály spuštění operace přetahování myší, pomocí pravým tlačítkem myši|  
|TVN_DELETEITEM|Signály odstranění konkrétní položky|  
|TVN_ENDLABELEDIT|Označuje konec úpravy štítků|  
|TVN_GETDISPINFO|Vyžaduje informace, že zobrazíte položky vyžaduje ovládací prvek stromu|  
|TVN_ITEMEXPANDED|Signály, že byl rozbalit nebo sbalit nadřazené položky seznamu podřízené položky|  
|TVN_ITEMEXPANDING|Signály, které nadřazené položky seznamu podřízené položky se chystá rozbalit nebo sbalit|  
|TVN_KEYDOWN|Signály události klávesnice|  
|TVN_SELCHANGED|Signály, které výběr se změnil z jednu položku na jiný|  
|TVN_SELCHANGING|Signály, které je výběr Chystáte se změnit z jednu položku na jiný|  
|TVN_SETDISPINFO|Oznámení aktualizovat informace o udržuje pro položku|  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

