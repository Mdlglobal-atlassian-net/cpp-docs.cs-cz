---
title: Zpracování oznámení ovládacího prvku záhlaví
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
ms.openlocfilehash: bc811763fe3f4717b8baaeb4a23df1ae59bb1979
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908125"
---
# <a name="processing-header-control-notifications"></a>Zpracování oznámení ovládacího prvku záhlaví

Ve vaší třídě zobrazení nebo dialogového okna použijte [Průvodce třídami](reference/mfc-class-wizard.md) k vytvoření funkce obslužné rutiny [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) s příkazem Switch pro všechny oznamovací zprávy řízení hlaviček ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)), které chcete zpracovat (viz [mapování zpráv na Funkce](../mfc/reference/mapping-messages-to-functions.md)). Oznámení se odesílají do nadřazeného okna, když uživatel klikne nebo dvakrát klikne na položku záhlaví, přetahuje oddělovač mezi položkami a tak dále.

Oznamovací zprávy přidružené k ovládacímu prvku záhlaví jsou uvedeny v [odkazu ovládacího prvku záhlaví](/windows/win32/controls/header-control-reference) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
