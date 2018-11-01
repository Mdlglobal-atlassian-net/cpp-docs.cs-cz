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
ms.openlocfilehash: 4513bafedd531c7f0bcb103728c19c0940a2efc9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626769"
---
# <a name="processing-header-control-notifications"></a>Zpracování oznámení ovládacího prvku záhlaví

Ve třídě zobrazení nebo dialogovém okně, použijte okno Vlastnosti k vytvoření [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkci obslužné rutiny pomocí příkazu switch pro jakékoli záhlaví ovládacího prvku ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) chcete zpráv s oznámením zpracování (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)). Oznámení se posílají nadřazenému oknu, když uživatel klepne nebo dvakrát klikne položky záhlaví, drags a oddělovač mezi položkami a tak dále.

Upozornění související s ovládacím prvkem záhlaví jsou uvedeny v [záhlaví ovládacího prvku odkazu](https://msdn.microsoft.com/library/windows/desktop/bb775239) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

