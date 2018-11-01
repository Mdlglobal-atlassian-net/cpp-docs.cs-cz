---
title: Správa aktuálního zobrazení
ms.date: 11/04/2016
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
ms.openlocfilehash: c53193a2e8121274246eabd9c7b614ad986146c0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575484"
---
# <a name="managing-the-current-view"></a>Správa aktuálního zobrazení

Jako součást výchozí implementace oken s rámečkem uchovává informace okno rámce o aktuálně aktivní zobrazení. Pokud obsahuje více než jedno zobrazení, například v okně rozdělovač okna rámce aktuálního zobrazení se zobrazení posledního použití. Aktivní zobrazení je nezávislá aktivního okna ve Windows nebo aktuální vstupní fokus.

Aktivní zobrazení změny, rozhraní upozorní aktuální zobrazení po zavolání jeho [OnActivateView](../mfc/reference/cview-class.md#onactivateview) členskou funkci. Poznáte, zda je zobrazení se aktivuje nebo deaktivuje prozkoumáním `OnActivateView`společnosti *bActivate* parametru. Ve výchozím nastavení `OnActivateView` nastaví fokus na aktuální zobrazení na aktivaci. Můžete přepsat `OnActivateView` provést žádné speciální zpracování při zobrazení je deaktivováno nebo znovu aktivovat. Například můžete chtít poskytnout speciální vizuálních podnětů k rozlišení zobrazení aktivního ze zobrazení, které neaktivní.

Okno rámce předává příkazy do jeho aktuálního zobrazení (aktivní), jak je popsáno v [směrování příkazů](../mfc/command-routing.md), jako součást standardního směrování příkazů.

## <a name="see-also"></a>Viz také

[Použití oken s rámečkem](../mfc/using-frame-windows.md)

