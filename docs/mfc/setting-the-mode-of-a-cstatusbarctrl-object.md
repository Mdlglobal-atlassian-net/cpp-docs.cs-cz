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
ms.openlocfilehash: a6d1a0edb356f9737aa287809dd8bca4146c1854
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307715"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Nastavení režimu objektu CStatusBarCtrl

Existují dva režimy pro `CStatusBarCtrl` objektu: jednoduché a nejednoduché. Ve většině případů bude mít ovládací prvek panelu Stav jednu nebo více částí, spolu s textem a možná ikonu nebo ikony. Tomu se říká nejednoduché režimu. Další informace o tomto režimu najdete v tématu [inicializace částí objektu CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).

Existují však případy, kdy je potřeba jenom zobrazí jeden řádek textu. Jednoduchý režim v takovém případě stačí pro vaše potřeby. Chcete-li změnit režim `CStatusBarCtrl` objektu na hodnotu simple, volání [setsimple –](../mfc/reference/cstatusbarctrl-class.md#setsimple) členskou funkci. Jakmile ovládací prvek panelu stavu v stručném režimu, nastavení textu voláním `SetText` členská funkce, jako hodnotu pro předání 255 *nPane* parametru.

Můžete použít [issimple –](../mfc/reference/cstatusbarctrl-class.md#issimple) funkce k určení režimu `CStatusBarCtrl` objekt je v.

> [!NOTE]
>  Pokud se stav objektu panelu se mění z nonsimple na jednoduchý, nebo naopak, okamžitě překreslení okna a pokud je k dispozici žádné definované součásti se automaticky obnoví.

## <a name="see-also"></a>Viz také:

[Používání atributu CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
