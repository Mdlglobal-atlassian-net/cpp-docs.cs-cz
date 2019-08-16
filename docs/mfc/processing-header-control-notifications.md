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
ms.openlocfilehash: f60a0c918476702881984f976b220130727cf4b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507949"
---
# <a name="processing-header-control-notifications"></a>Zpracování oznámení ovládacího prvku záhlaví

Ve vaší třídě zobrazení nebo dialogového okna použijte okno Vlastnosti k vytvoření funkce obslužné rutiny [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) s příkazem Switch pro jakékoli oznamovací zprávy řízení hlaviček ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)), které chcete zpracovat (viz téma [mapování zpráv na funkce ](../mfc/reference/mapping-messages-to-functions.md)). Oznámení se odesílají do nadřazeného okna, když uživatel klikne nebo dvakrát klikne na položku záhlaví, přetahuje oddělovač mezi položkami a tak dále.

Oznamovací zprávy přidružené k ovládacímu prvku záhlaví jsou uvedeny v [odkazu ovládacího prvku záhlaví](/windows/win32/controls/header-control-reference) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
