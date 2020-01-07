---
title: Použití dialogového pruhu s ovládacím prvkem matrice
ms.date: 11/04/2016
helpviewer_keywords:
- WS_EX_TRANSPARENT style
- rebar controls [MFC], dialog bars
- dialog bars [MFC], using with rebar bands
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
ms.openlocfilehash: e4e786d3670ec74b734739e29aa7e3e33b5af384
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302364"
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>Použití dialogového pruhu s ovládacím prvkem matrice

Jak je uvedeno v [ovládacích prvcích a pásmech matrice](../mfc/rebar-controls-and-bands.md), každý pruh může obsahovat pouze jedno podřízené okno (nebo ovládací prvek). To může být omezení, pokud chcete mít více než jedno podřízené okno na jeden panel. Pohodlným řešením je vytvořit prostředek panelu nástrojů s více ovládacími prvky a následně přidat matrice panel (obsahující panel dialogového okna) do ovládacího prvku matrice.

Pokud byste chtěli, aby se pruh panelu dialogového okna zobrazil jako průhledný, nastavili jste pro objekt panelu dialogového okna rozšířený styl WS_EX_TRANSPARENT. Vzhledem k tomu, že WS_EX_TRANSPARENT obsahuje nějaké problémy s řádným vykreslením pozadí panelu nástrojů, budete muset provést trochu další práci, abyste dosáhli požadovaného účinku.

Následující postup podrobně popisuje kroky potřebné k dosažení transparentnosti bez použití rozšířeného stylu WS_EX_TRANSPARENT.

### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>Implementace transparentního dialogového okna v matrice pásmu

1. Pomocí [dialogového okna Přidat třídu](../mfc/reference/adding-an-mfc-class.md)přidejte novou třídu (například `CMyDlgBar`), která implementuje objekt panelu dialogového okna.

1. Přidejte obslužnou rutinu pro WM_ERASEBKGNDovou zprávu.

1. V nové obslužné rutině upravte existující kód tak, aby odpovídal následujícímu příkladu:

   [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]

1. Přidejte obslužnou rutinu pro WM_MOVEovou zprávu.

1. V nové obslužné rutině upravte existující kód tak, aby odpovídal následujícímu příkladu:

   [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]

Nové obslužné rutiny simulují průhlednost panelu dialogového okna tím, že předají zprávu WM_ERASEBKGND do nadřazeného okna a vynutí překreslení pokaždé, když se objekt panelu dialogového okna přesune.

## <a name="see-also"></a>Viz také:

[Používání atributu CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
