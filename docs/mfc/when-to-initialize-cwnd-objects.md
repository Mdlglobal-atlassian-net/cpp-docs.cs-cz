---
title: Kdy je třeba inicializovat objekty CWnd
ms.date: 11/04/2016
helpviewer_keywords:
- window objects [MFC], when to initialize CWnd
- initializing CWnd objects [MFC]
- initializing objects [MFC], CWnd
- CWnd objects [MFC], when HWND is attached
- HWND, when attached to CWnd object
- CWnd objects [MFC], when to initialize
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
ms.openlocfilehash: aa396ade2e8ab4e1245e161423de7bd5bfafaaf8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57291344"
---
# <a name="when-to-initialize-cwnd-objects"></a>Kdy je třeba inicializovat objekty CWnd

Nemůžete vytvořit vlastní podřízené windows ani volat jakékoli funkce rozhraní Windows API v konstruktoru `CWnd`-odvozenému objektu. Je to proto, `HWND` pro `CWnd` objekt ještě nebyl vytvořen. Inicializace nejvíce specifické pro Windows, jako je například přidávání podřízených oken, je třeba provést v [OnCreate](../mfc/reference/cwnd-class.md#oncreate) obslužné rutiny zpráv.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Vytváření oken s rámečkem v dokumentu](../mfc/creating-document-frame-windows.md)

- [Vytváření dokumentů/zobrazení](../mfc/document-view-creation.md)

## <a name="see-also"></a>Viz také:

[Použití oken s rámečkem](../mfc/using-frame-windows.md)
