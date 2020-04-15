---
title: Nastavení pro třídu CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
ms.openlocfilehash: dd7c68d6721c48f751c04437e43c8770f6ec5736
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365381"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Nastavení pro třídu CStatusBarCtrl

Výchozí pozice stavového okna [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) se nachází v dolní části nadřazeného okna, ale můžete určit CCS_TOP styl, aby se zobrazil v horní části klientské oblasti nadřazeného okna.

Můžete určit styl SBARS_SIZEGRIP, který bude obsahovat uzel `CStatusBarCtrl` pro změnu velikosti na pravém konci stavového okna. Uzel velikosti je podobný ohraničení velikosti; jedná se o obdélníkovou oblast, na kterou může uživatel klepnout a přetáhnout a změnit velikost nadřazeného okna.

> [!NOTE]
> Pokud zkombinujete styly CCS_TOP a SBARS_SIZEGRIP, výsledný uzel pro změnu velikosti není funkční, i když jej systém nakreslí ve stavovém okně.

Postup okna pro stavové okno automaticky nastaví počáteční velikost a umístění ovládacího okna. Šířka je stejná jako šířka klientské oblasti nadřazeného okna. Výška je založena na metriky písma, které je aktuálně vybráno do kontextu zařízení stavového okna a na šířce ohraničení okna.

Procedura okna automaticky upraví velikost stavového okna vždy, když obdrží zprávu WM_SIZE. Obvykle při změně velikosti nadřazeného okna, nadřazený odešle zprávu WM_SIZE do okna stavu.

Minimální výšku kreslicí plochy stavového okna můžete nastavit voláním [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight)a určením minimální výšky v obrazových bodech. Kreslicí plocha neobsahuje ohraničení okna.

Šířky ohraničení stavového okna načtete voláním [GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders). Tato členská funkce obsahuje ukazatel na pole se třemi prvky, které přijímá šířku vodorovného ohraničení, svislého ohraničení a ohraničení mezi obdélníky.

## <a name="see-also"></a>Viz také

[Používání atributu CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
