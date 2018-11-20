---
title: Správa podřízených oken MDI
ms.date: 11/19/2018
f1_keywords:
- MDICLIENT
helpviewer_keywords:
- MDI [MFC], child windows
- child windows [MFC], and MDICLIENT window
- MDICLIENT window [MFC]
- windows [MFC], MDI
- frame windows [MFC], MDI child windows
- child windows [MFC]
- MDI [MFC], frame windows
ms.assetid: 1828d96e-a561-48ae-a661-ba9701de6bee
ms.openlocfilehash: d4b6ccf8a75cc7679f78fba48314073bc53b66a5
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176793"
---
# <a name="managing-mdi-child-windows"></a>Správa podřízených oken MDI

Okna hlavního rámce MDI, (jeden na aplikaci) obsahují speciální podřízeného okna okno MDICLIENT volána. Okno MDICLIENT spravuje klientské oblasti okna hlavního rámce a samotné má podřízená okna: okna dokumentů, odvozený z `CMDIChildWnd`. Protože okna dokumentu jsou oken s rámečkem v samotných (podřízených oken MDI), budou také obsahovat vlastní podřízené položky. Ve všech těchto případech nadřazené okno spravuje jeho podřízených oken a předává některé příkazy k nim.

V okně rámce MDI spravuje oknem rámce okno MDICLIENT přemístění ve spojení s ovládací panely. Okno MDICLIENT zase slouží ke správě všech podřízených oken rámce MDI. Následující obrázek ukazuje vztah mezi okna rámce MDI, jeho okno MDICLIENT a jeho podřízených oken rámce dokumentu.

![Podřízená okna v okně rámce MDI](../mfc/media/vc37gb1.gif "podřízená okna v okně rámce MDI") <br/>
Rámce Windows MDI a podřízené položky

Okna rámce MDI je také funguje ve spojení s aktuální podřízené okno MDI, pokud existuje. Okno rámce MDI deleguje příkaz zprávy do podřízeného MDI předtím, než se pokusí zpracovat samotný.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Vytváření oken s rámečkem v dokumentu](../mfc/creating-document-frame-windows.md)

- [Styly oken s rámečkem](../mfc/frame-window-styles-cpp.md)

## <a name="see-also"></a>Viz také

[Použití oken s rámečkem](../mfc/using-frame-windows.md)

