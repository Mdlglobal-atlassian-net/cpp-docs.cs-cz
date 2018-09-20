---
title: Strom zpráv s oznámením ovládacího prvku | Dokumentace Microsoftu
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
ms.openlocfilehash: 07911dec25bf9d6b80f025e2f3738e3d98ffd2cb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390744"
---
# <a name="tree-control-notification-messages"></a>Zprávy s oznámením ovládacího prvku strom

Ovládací prvek stromu ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) odešle tyto zprávy s oznámením jako wm_notify – zprávy:

|Oznámení|Popis|
|--------------------------|-----------------|
|TVN_BEGINDRAG|Signály zahájení operace přetažení myší|
|TVN_BEGINLABELEDIT|Označuje začátek úpravy na místě štítků|
|TVN_BEGINRDRAG|Signály zahájení operace přetažení myší, pomocí pravé tlačítko myši|
|TVN_DELETEITEM|Signály odstranění konkrétní položky|
|TVN_ENDLABELEDIT|Signalizuje konec úpravy štítků|
|TVN_GETDISPINFO|Požádá o informace, že ovládací prvek stromu vyžaduje k zobrazení položek|
|TVN_ITEMEXPANDED|Signály, že se nadřazená položka seznamu podřízených položek rozbalit nebo sbalit|
|TVN_ITEMEXPANDING|Signály, které nadřazená položka seznamu podřízených položek se chystá rozbalit nebo sbalit|
|TVN_KEYDOWN|Signály události klávesnice|
|TVN_SELCHANGED|Signály, které se změní výběr z jedné položky do jiného|
|TVN_SELCHANGING|Signály, které je výběr Chystáte se změnit z jedné položky do jiného|
|TVN_SETDISPINFO|Oznámení aktualizace informací uchovávaných položky|

## <a name="see-also"></a>Viz také

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

