---
title: Když třeba inicializovat objekty CWnd | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window objects [MFC], when to initialize CWnd
- initializing CWnd objects [MFC]
- initializing objects [MFC], CWnd
- CWnd objects [MFC], when HWND is attached
- HWND, when attached to CWnd object
- CWnd objects [MFC], when to initialize
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6445190ab3da6ed84dbdd83cd0acab0ba98691f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388430"
---
# <a name="when-to-initialize-cwnd-objects"></a>Kdy je třeba inicializovat objekty CWnd

Nemůžete vytvořit vlastní podřízené windows ani volat jakékoli funkce rozhraní Windows API v konstruktoru `CWnd`-odvozenému objektu. Je to proto, `HWND` pro `CWnd` objekt ještě nebyl vytvořen. Inicializace nejvíce specifické pro Windows, jako je například přidávání podřízených oken, je třeba provést v [OnCreate](../mfc/reference/cwnd-class.md#oncreate) obslužné rutiny zpráv.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Vytváření oken s rámečkem v dokumentu](../mfc/creating-document-frame-windows.md)

- [Vytváření dokumentů/zobrazení](../mfc/document-view-creation.md)

## <a name="see-also"></a>Viz také

[Použití oken s rámečkem](../mfc/using-frame-windows.md)

