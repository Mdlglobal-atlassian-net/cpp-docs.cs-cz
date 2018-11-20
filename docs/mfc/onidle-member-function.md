---
title: OnIdle – členská funkce
ms.date: 11/19/2018
f1_keywords:
- OnIdle
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
ms.openlocfilehash: 7b3f2fbeac6ae356003abf12b5df4c54c8bb327a
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175130"
---
# <a name="onidle-member-function"></a>OnIdle – členská funkce

Při zpracování zprávy bez Windows se volá framework [CWinApp](../mfc/reference/cwinapp-class.md) členskou funkci [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (podle Reference knihovny MFC).

Přepsat `OnIdle` k provedení úlohy na pozadí. Výchozí verze aktualizace stavu objektů uživatelského rozhraní, jako jsou tlačítka na panelu nástrojů a provádí vyčištění dočasné objekty vytvořené v rámci rozhraní tím jeho operace. Následující obrázek znázorňuje, jakým způsobem volá smyčky zpráv `OnIdle` při nejsou žádné zprávy ve frontě.

![Proces smyčky zpráv](../mfc/media/vc387c1.gif "proces smyčky zpráv") <br/>
Smyčky zpráv

Další informace o tom, co můžete učinit nečinné smyčky, naleznete v tématu [zpracování nečinné smyčky](../mfc/idle-loop-processing.md).

## <a name="see-also"></a>Viz také

[CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
