---
title: Nastavení pro ovládací prvek popis tlačítka
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], activating
- CToolTipCtrl class [MFC], settings
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
ms.openlocfilehash: 5cc72401da95e63520b544865ea509a8ad219bda
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307611"
---
# <a name="settings-for-the-tool-tip-control"></a>Nastavení pro ovládací prvek popis tlačítka

Můžete nastavit ovládacím prvkem popis tlačítka nástroje ([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)) Chcete-li být aktivní nebo neaktivní. Když se nastavuje jako aktivní, ovládacím prvkem popis tlačítka nástroje se zobrazí, když ukazatel zůstane na nástroj. Pokud ji do neaktivního stavu, ovládacím prvkem popis tlačítka nástroje nezobrazí, i když ukazatel zůstane na nástroj. Volání [aktivovat](../mfc/reference/ctooltipctrl-class.md#activate) aktivovat nebo deaktivovat ovládacím prvkem popis tlačítka nástroj.

Můžete nastavit aktivní popis tlačítka, který zobrazí popis tlačítka, když je ukazatel myši na nástroje, zda okno vlastníka ovládacím prvkem popis tlačítka nástroj je aktivní nebo neaktivní, s použitím stylu TTS_ALWAYSTIP. Pokud nepoužijete tento styl, zobrazí se ovládacím prvkem popis tlačítka nástroj při aktivním nástroje nadřazenému oknu, ale ne v případě, že je neaktivní.

Většina aplikací obsahují panely nástrojů s nástroji, které odpovídají nabídce příkazů. Pro takové nástroje je vhodné pro ovládacím prvkem popis tlačítka nástroj zobrazit stejný text jako příslušnou položku. Systém automaticky odstraní ampersand (&) akcelerátoru znaků z řetězců všechny předán ovládacím prvkem popis tlačítka nástroj, pokud ovládací prvek nemá TTS_NOPREFIX style.

## <a name="see-also"></a>Viz také:

[Používání atributu CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
