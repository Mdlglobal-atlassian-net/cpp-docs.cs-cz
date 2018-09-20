---
title: Zpracování zpráv s oznámením ovládacího prvku karta | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], tab controls
- CTabCtrl class [MFC], processing notifications
- notifications [MFC], processing in CTabCtrl
- processing notifications [MFC]
- tab controls [MFC], processing notifications
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 258a3ee579eca0262dace6d1e69a3b5daf9024f6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409035"
---
# <a name="processing-tab-control-notification-messages"></a>Zpracování zpráv s oznámením ovládacího prvku karta

Jak uživatelé kliknou na kartách nebo tlačítka, ovládacího prvku karta ([atributu CTabCtrl](../mfc/reference/ctabctrl-class.md)) odesílá zprávy s oznámením nezašle nadřazenému oknu. Tyto zprávy zpracovávají, pokud budete chtít udělat něco v odpovědi. Když uživatel klikne na kartu, můžete chtít přednastavení data ovládací prvek na stránce před zobrazením.

Zpracovat wm_notify – zprávy z ovládacího prvku karta ve třídě zobrazení nebo dialogového okna. Okno Vlastnosti použít k vytvoření [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkci obslužné rutiny pomocí příkazu switch podle zpráv oznámení, které se právě zpracovává. Seznam oznámení ovládacího prvku karta může odeslat nezašle nadřazenému oknu, najdete v článku **oznámení** část [ovládací prvek karty](https://msdn.microsoft.com/library/windows/desktop/bb760548) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Používání atributu CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

