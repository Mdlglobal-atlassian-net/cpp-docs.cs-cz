---
title: Nastavení pro třídu CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
ms.openlocfilehash: 18c4c780ecf7865d8d648bfa4c54961bbffe7b18
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446398"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Nastavení pro třídu CStatusBarCtrl

Výchozí pozice stavového okna [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) je podél dolního okraje nadřazeného okna, ale můžete určit styl CCS_TOP, který se zobrazí v horní části klientské oblasti nadřazeného okna.

Můžete určit styl SBARS_SIZEGRIP pro zahrnutí úchytu pro změnu velikosti na pravé straně okna stavu `CStatusBarCtrl`. Úchyt pro změnu velikosti je podobný hranici velikosti; Jedná se o obdélníkovou oblast, kterou uživatel může kliknutím a přetažením změnit velikost nadřazeného okna.

> [!NOTE]
>  Pokud kombinujete styly CCS_TOP a SBARS_SIZEGRIP, výsledné úchyty pro změnu velikosti nebudou funkční, i když ho systém vykreslí v okně stav.

Procedura okna pro stavové okno automaticky nastaví počáteční velikost a polohu okna ovládacího prvku. Šířka je stejná jako v klientské oblasti v nadřazeném okně. Výška je založena na metrikách písma, které je aktuálně vybráno v kontextu zařízení stavového okna a na šířku ohraničení okna.

Procedura okna automaticky upraví velikost stavového okna vždy, když obdrží zprávu WM_SIZE. Obvykle při změně velikosti nadřazeného okna pošle nadřazená zpráva WM_SIZE do okna stavu.

Můžete nastavit minimální výšku oblasti kreslení stavového okna voláním [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight)a určením minimální výšky v pixelech. Oblast kreslení neobsahuje ohraničení okna.

Načtěte šířky ohraničení stavového okna voláním [GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders). Tato členská funkce zahrnuje ukazatel na pole se třemi prvky, které přijímá šířku vodorovného ohraničení, svislé ohraničení a ohraničení mezi obdélníky.

## <a name="see-also"></a>Viz také

[Používání atributu CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
