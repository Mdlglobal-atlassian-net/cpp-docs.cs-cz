---
title: Použití dialogového pruhu s ovládacím prvkem matrice
ms.date: 11/04/2016
f1_keywords:
- WM_EX_TRANSPARENT
helpviewer_keywords:
- WS_EX_TRANSPARENT style
- rebar controls [MFC], dialog bars
- dialog bars [MFC], using with rebar bands
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
ms.openlocfilehash: 33ca3d0a7bf2e60511ea0048ad91b1f0930a2894
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287172"
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>Použití dialogového pruhu s ovládacím prvkem matrice

Jak je uvedeno v [matrice – ovládací prvky a pruhy](../mfc/rebar-controls-and-bands.md), každý obsluhy vzdálené správy může obsahovat pouze jeden podřízené okno (nebo ovládací prvek). To může být omezení, pokud chcete mít více než jeden podřízené okno za obsluhy vzdálené správy. Pohodlné alternativním řešením je vytvoření prostředku panel dialogového okna pomocí více ovládacích prvků a pak přidejte matrice obsluhy vzdálené správy (který obsahuje panel dialogového okna) do ovládacího prvku rebar.

Za normálních okolností kdybys chtěla vzdálené panel dialogového okna se zobrazí transparentní, nastavíte WS_EX_TRANSPARENT rozšířený styl pro objekt panel dialogového okna. Ale protože WS_EX_TRANSPARENT má některé problémy s správně vykreslování pozadí panel dialogového okna, je potřeba udělat trochu práce navíc k dosažení požadovaného efektu.

Následující podrobnosti o postupu kroky potřebné k dosažení transparentnosti bez použití WS_EX_TRANSPARENT rozšířený styl.

### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>K implementaci transparentní dialogového pruhu ve svazku matrice

1. Použití [dialogové okno Přidat třídu](../mfc/reference/adding-an-mfc-class.md), přidejte novou třídu (například `CMyDlgBar`), který implementuje objekt panel dialogového okna.

1. Přidání obslužné rutiny pro zprávy WM_ERASEBKGND.

1. V nové obslužné rutiny upravte existující kód tak, aby odpovídaly v následujícím příkladu:

   [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]

1. Přidání obslužné rutiny pro zprávy WM_MOVE.

1. V nové obslužné rutiny upravte existující kód tak, aby odpovídaly v následujícím příkladu:

   [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]

Nové obslužné rutiny simulovat transparentnosti panel dialogového okna předávání WM_ERASEBKGND zprávu nadřazenému oknu a vynucení repaint pokaždé, když je přesunut objektu panel dialogového okna.

## <a name="see-also"></a>Viz také:

[Používání atributu CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
