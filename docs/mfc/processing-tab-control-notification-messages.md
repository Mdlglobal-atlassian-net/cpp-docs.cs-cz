---
title: Zpracování zpráv s oznámením ovládacího prvku karta
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], tab controls
- CTabCtrl class [MFC], processing notifications
- notifications [MFC], processing in CTabCtrl
- processing notifications [MFC]
- tab controls [MFC], processing notifications
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
ms.openlocfilehash: 32e1b5954bc3f09f16c5516fc1c143dac716bc41
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693229"
---
# <a name="processing-tab-control-notification-messages"></a>Zpracování zpráv s oznámením ovládacího prvku karta

Jak uživatelé kliknou na kartách nebo tlačítka, ovládacího prvku karta ([atributu CTabCtrl](../mfc/reference/ctabctrl-class.md)) odesílá zprávy s oznámením nezašle nadřazenému oknu. Tyto zprávy zpracovávají, pokud budete chtít udělat něco v odpovědi. Když uživatel klikne na kartu, můžete chtít přednastavení data ovládací prvek na stránce před zobrazením.

Zpracovat wm_notify – zprávy z ovládacího prvku karta ve třídě zobrazení nebo dialogového okna. Okno Vlastnosti použít k vytvoření [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkci obslužné rutiny pomocí příkazu switch podle zpráv oznámení, které se právě zpracovává. Seznam oznámení ovládacího prvku karta může odeslat nezašle nadřazenému oknu, najdete v článku **oznámení** část [ovládací prvek karty](/windows/desktop/controls/tab-control-reference) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Používání atributu CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

