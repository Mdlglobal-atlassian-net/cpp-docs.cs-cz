---
title: Nastavení pro třídu CStatusBarCtrl | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2411659e6ae33fe9ce81d508d3e7c206b1e5b113
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440027"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Nastavení pro třídu CStatusBarCtrl

Výchozí pozice [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) podél dolního okraje nadřazeného okna se stavové okno, ale můžete určit styl CCS_TOP na něm se zobrazí v horní části klientské oblasti okna nadřazené.

Můžete určit styl SBARS_SIZEGRIP zahrnout úchyt na pravém konci `CStatusBarCtrl` stavové okno. Úchyt pro změnu velikosti je podobná velikosti ohraničení; je obdélníkovou oblast, která uživatel může klikněte a přetáhněte pro změnu velikosti nadřazeného okna.

> [!NOTE]
>  Pokud kombinujete CCS_TOP a SBARS_SIZEGRIP styly, výsledný úchyt pro změnu velikosti není funkční, přestože systém nakreslí ho v okně Stav.

Proceduru okna pro stavové okno automaticky nastaví počáteční velikost a umístění okna ovládacího prvku. Šířka je stejné jako u nadřazené okno klientské oblasti. Výška je založena na metriky písma, která je aktuálně vybrána v kontextu zařízení stavové okno a na šířku ohraničení okna.

Proceduru okna velikost stavové okno automaticky přizpůsobí pokaždé, když dostane zprávu WM_SIZE. Obvykle při změně velikosti nadřazené okno nadřazené odešle zprávu WM_SIZE stavové okno.

Můžete nastavit minimální výšku oblasti pro kreslení stavové okno voláním [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight), určení minimální výšku v pixelech. Vykreslení oblasti nezahrnuje ohraničení okna.

Načíst šířky ohraničení stavové okno voláním [GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders). Tato členská funkce obsahuje ukazatel na prvek tři pole, která přijímá šířku ohraničení vodorovné, svislé ohraničení a ohraničení mezi obdélníky.

## <a name="see-also"></a>Viz také

[Používání atributu CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

