---
title: Zpracování zpráv s oznámením v ovládacích prvcích seznamů
ms.date: 11/04/2016
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
ms.openlocfilehash: e93e91a3219f81bf4027549fc84f1c85c8defb5b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507874"
---
# <a name="processing-notification-messages-in-list-controls"></a>Zpracování zpráv s oznámením v ovládacích prvcích seznamů

Když uživatel klikne na záhlaví sloupců, přetáhnout ikony, upravit popisky a tak dále, ovládací prvek seznam ([CListCtrl](../mfc/reference/clistctrl-class.md)) odesílá zprávy s oznámením do svého nadřazeného okna. Pokud chcete něco udělat v reakci, Zpracujte tyto zprávy. Například když uživatel klikne na záhlaví sloupce, možná budete chtít seřadit položky na základě obsahu sloupce po kliknutí, jako v aplikaci Microsoft Outlook.

Zpracujte zprávy WM_NOTIFY z ovládacího prvku seznamu ve vaší třídě zobrazení nebo dialogového okna. Použijte okno Vlastnosti k vytvoření funkce obslužné rutiny [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) s příkazem Switch na základě toho, kterou zprávu oznámení zpracovává.

Seznam oznámení, která může ovládací prvek seznamu odeslat do svého nadřazeného okna, najdete v tématu [odkazy na ovládací prvky zobrazení seznamu](/windows/win32/Controls/list-view-control-reference) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Používání atributu CListCtrl](../mfc/using-clistctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
