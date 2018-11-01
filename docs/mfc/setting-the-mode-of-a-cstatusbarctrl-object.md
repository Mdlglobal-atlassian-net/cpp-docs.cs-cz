---
title: Nastavení režimu objektu CStatusBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
ms.openlocfilehash: 0009f73f11b1a3c57f5001269f34834c22b045c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655248"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Nastavení režimu objektu CStatusBarCtrl

Existují dva režimy pro `CStatusBarCtrl` objektu: jednoduché a nejednoduché. Ve většině případů bude mít ovládací prvek panelu Stav jednu nebo více částí, spolu s textem a možná ikonu nebo ikony. Tomu se říká nejednoduché režimu. Další informace o tomto režimu najdete v tématu [inicializace částí objektu CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).

Existují však případy, kdy je potřeba jenom zobrazí jeden řádek textu. Jednoduchý režim v takovém případě stačí pro vaše potřeby. Chcete-li změnit režim `CStatusBarCtrl` objektu na hodnotu simple, volání [setsimple –](../mfc/reference/cstatusbarctrl-class.md#setsimple) členskou funkci. Jakmile ovládací prvek panelu stavu v stručném režimu, nastavení textu voláním `SetText` členská funkce, jako hodnotu pro předání 255 *nPane* parametru.

Můžete použít [issimple –](../mfc/reference/cstatusbarctrl-class.md#issimple) funkce k určení režimu `CStatusBarCtrl` objekt je v.

> [!NOTE]
>  Pokud se stav objektu panelu se mění z nonsimple na jednoduchý, nebo naopak, okamžitě překreslení okna a pokud je k dispozici žádné definované součásti se automaticky obnoví.

## <a name="see-also"></a>Viz také

[Používání atributu CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

