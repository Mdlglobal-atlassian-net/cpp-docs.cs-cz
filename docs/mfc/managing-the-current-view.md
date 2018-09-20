---
title: Správa aktuálního zobrazení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], and OnActivateView method [MFC]
- views [MFC], deactivating
- views [MFC], activating
- frame windows [MFC], current view
- OnActivateView method [MFC]
- views [MFC], current
- deactivating views [MFC]
- current view in frame window [MFC]
ms.assetid: 0a1cc22d-d646-4536-9ad2-3cb6d7092e4a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca9738f9b6083ef88c2f72e1608121f849f8e909
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425362"
---
# <a name="managing-the-current-view"></a>Správa aktuálního zobrazení

Jako součást výchozí implementace oken s rámečkem uchovává informace okno rámce o aktuálně aktivní zobrazení. Pokud obsahuje více než jedno zobrazení, například v okně rozdělovač okna rámce aktuálního zobrazení se zobrazení posledního použití. Aktivní zobrazení je nezávislá aktivního okna ve Windows nebo aktuální vstupní fokus.

Aktivní zobrazení změny, rozhraní upozorní aktuální zobrazení po zavolání jeho [OnActivateView](../mfc/reference/cview-class.md#onactivateview) členskou funkci. Poznáte, zda je zobrazení se aktivuje nebo deaktivuje prozkoumáním `OnActivateView`společnosti *bActivate* parametru. Ve výchozím nastavení `OnActivateView` nastaví fokus na aktuální zobrazení na aktivaci. Můžete přepsat `OnActivateView` provést žádné speciální zpracování při zobrazení je deaktivováno nebo znovu aktivovat. Například můžete chtít poskytnout speciální vizuálních podnětů k rozlišení zobrazení aktivního ze zobrazení, které neaktivní.

Okno rámce předává příkazy do jeho aktuálního zobrazení (aktivní), jak je popsáno v [směrování příkazů](../mfc/command-routing.md), jako součást standardního směrování příkazů.

## <a name="see-also"></a>Viz také

[Použití oken s rámečkem](../mfc/using-frame-windows.md)

