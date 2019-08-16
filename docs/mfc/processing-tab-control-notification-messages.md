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
ms.openlocfilehash: 97abde8285a3baf307df79fd97d4f9a379c8f58f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507836"
---
# <a name="processing-tab-control-notification-messages"></a>Zpracování zpráv s oznámením ovládacího prvku karta

Když uživatel klikne na karty nebo tlačítka, ovládací prvek karta ([atributu CTabCtrl](../mfc/reference/ctabctrl-class.md)) odesílá zprávy s oznámením do svého nadřazeného okna. Pokud chcete něco udělat v reakci, Zpracujte tyto zprávy. Například když uživatel klikne na kartu, možná budete chtít před zobrazením na stránce přednastavit data ovládacího prvku.

Zpracujte zprávy WM_NOTIFY z ovládacího prvku karta ve vaší třídě zobrazení nebo dialogového okna. Použijte okno Vlastnosti k vytvoření funkce obslužné rutiny [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) s příkazem Switch na základě toho, kterou zprávu oznámení zpracovává. Seznam oznámení, která může ovládací prvek karta poslat do svého nadřazeného okna, najdete v části **oznámení** [odkazu na ovládací prvek karty](/windows/win32/controls/tab-control-reference) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Používání atributu CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
