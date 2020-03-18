---
title: Třídy ovládacích pruhů
ms.date: 11/04/2016
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
ms.openlocfilehash: a050c5d2f7396324c2c380a03fc28e01ab992208
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440965"
---
# <a name="control-bar-classes"></a>Třídy ovládacích pruhů

Ovládací panely jsou připojeny k oknu rámce. Obsahují tlačítka, stavová podokna nebo šablonu dialogového okna. Bezplatné ovládací prvky, které jsou označovány také jako palety nástrojů, jsou implementovány připojením k objektu [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md) .

## <a name="framework-control-bars"></a>Řídicí panely rozhraní

Tyto ovládací panely jsou nedílnou součástí architektury MFC. Je jednodušší používat a výkonnější než ovládací panely Windows, protože jsou integrovány s architekturou. Většina aplikací MFC používá ovládací panely místo ovládacích panelů systému Windows.

[CControlBar –](../mfc/reference/ccontrolbar-class.md)<br/>
Základní třída pro ovládací prvky MFC uvedená v této části. Ovládací panel je okno zarovnané na okraj okna rámce. Ovládací panel obsahuje buď podřízené ovládací prvky nebo ovládací prvky založené na `HWND`, které nejsou založené na `HWND`, například tlačítka panelu nástrojů.

[CDialogBar](../mfc/reference/cdialogbar-class.md)<br/>
Ovládací panel, který je založen na šabloně dialogového okna.

[CReBar –](../mfc/reference/crebar-class.md)<br/>
Podporuje panel nástrojů, který může obsahovat další podřízená okna ve formě ovládacích prvků.

[CToolBar –](../mfc/reference/ctoolbar-class.md)<br/>
Okna ovládacích prvků panelu nástrojů obsahující příkazová tlačítka rastrového obrázku, která nejsou založená na `HWND`. Většina aplikací MFC používá tuto třídu místo `CToolBarCtrl`.

[CStatusBar –](../mfc/reference/cstatusbar-class.md)<br/>
Základní třída pro okna ovládacích prvků stavového řádku. Většina aplikací MFC používá tuto třídu místo `CStatusBarCtrl`.

## <a name="windows-control-bars"></a>Ovládací panely Windows

Tyto ovládací panely jsou tenké obálky pro odpovídající ovládací prvky systému Windows. Vzhledem k tomu, že nejsou integrovány s architekturou, jsou těžší používat než výše uvedené ovládací panely. Většina aplikací MFC používá výše uvedené ovládací panely.

[Atributu CReBarCtrl](../mfc/reference/crebarctrl-class.md)<br/>
Implementuje vnitřní kontrolu objektu `CRebar`.

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
Horizontální okno, obvykle rozdělené do podoken, ve kterém aplikace může zobrazit stavové informace.

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
Poskytuje funkce pro běžný ovládací prvek panelu nástrojů systému Windows.

## <a name="related-classes"></a>Související třídy

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
Malé automaticky otevírané okno, které zobrazuje jeden řádek textu popisující účel nástroje v aplikaci.

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
Zpracovává trvalé úložiště dat dokovacího stavu pro ovládací panely.

## <a name="see-also"></a>Viz také

[Přehled třídy](../mfc/class-library-overview.md)
