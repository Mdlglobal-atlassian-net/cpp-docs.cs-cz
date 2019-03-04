---
title: Styly oken s rámečkem (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
ms.openlocfilehash: cade8e7e50779437feb73a94058dc62118c03c10
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274645"
---
# <a name="frame-window-styles-c"></a>Styly oken s rámečkem (C++)

Jsou vhodné pro většinu programů rámečkem získáte s použitím rozhraní framework, ale získáte větší flexibilitu s využitím pokročilých funkcí [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) a globální funkce MFC [afxregisterwndclass – ](../mfc/reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow` Členská funkce je `CWnd`.

Pokud použijete **WS_HSCROLL** a **WS_VSCROLL** styly do okna hlavního rámce, místo toho použijí se **MDICLIENT** okno tak uživatelům umožní posouvání, **MDICLIENT** oblasti.

Pokud v okně **FWS_ADDTOTITLE** je nastaven bit stylu (která je ve výchozím nastavení), zobrazení informuje okno rámce název pro zobrazení v záhlaví okna. na základě názvu zobrazení dokumentu.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Správa podřízených oken MDI (MDICLIENT)](../mfc/managing-mdi-child-windows.md), okna MDI rámce, který obsahuje podřízených oken MDI

- [Změna stylů okna vytvořeného rozhraním MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

- [Styly oken](../mfc/reference/styles-used-by-mfc.md#window-styles)

## <a name="see-also"></a>Viz také:

[Okna s rámečkem](../mfc/frame-windows.md)
