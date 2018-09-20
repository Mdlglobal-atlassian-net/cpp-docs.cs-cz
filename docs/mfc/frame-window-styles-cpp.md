---
title: Styly oken s rámečkem (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f0e4bde874fc563535b661108cb68edefd8d977
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385011"
---
# <a name="frame-window-styles-c"></a>Styly oken s rámečkem (C++)

Jsou vhodné pro většinu programů rámečkem získáte s použitím rozhraní framework, ale získáte větší flexibilitu s využitím pokročilých funkcí [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) a globální funkce MFC [afxregisterwndclass – ](../mfc/reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow` Členská funkce je `CWnd`.

Pokud použijete **WS_HSCROLL** a **WS_VSCROLL** styly do okna hlavního rámce, místo toho použijí se **MDICLIENT** okno tak uživatelům umožní posouvání, **MDICLIENT** oblasti.

Pokud v okně **FWS_ADDTOTITLE** je nastaven bit stylu (která je ve výchozím nastavení), zobrazení informuje okno rámce název pro zobrazení v záhlaví okna. na základě názvu zobrazení dokumentu.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Správa podřízených oken MDI (MDICLIENT)](../mfc/managing-mdi-child-windows.md), okna MDI rámce, který obsahuje podřízených oken MDI

- [Změna stylů okna vytvořeného rozhraním MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

- [Styly oken](../mfc/reference/styles-used-by-mfc.md#window-styles)

## <a name="see-also"></a>Viz také

[Okna s rámečkem](../mfc/frame-windows.md)

