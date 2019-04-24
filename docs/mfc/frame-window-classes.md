---
title: Třídy oken s rámečkem
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], about frame window classes
- frame window classes [MFC]
- windows [MFC], MDI
- document frame windows [MFC], classes
- single document interface (SDI), frame windows
- window classes [MFC], frame
- MFC, frame windows
- MDI [MFC], frame windows
- classes [MFC], window
ms.assetid: c27e43a7-8ad0-4759-b1b7-43f4725f4132
ms.openlocfilehash: d42fa475fca7c92e4ba46b164a9beda9869231c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219779"
---
# <a name="frame-window-classes"></a>Třídy oken s rámečkem

Každá aplikace má jeden "hlavní okno rámce," desktop okno, které obvykle název aplikace v titulek. Každý dokument obvykle má jednu "okno rámce dokumentu." Okno rámce dokumentu obsahuje alespoň jedno zobrazení, která představuje data dokumentu.

## <a name="frame-windows-in-sdi-and-mdi-applications"></a>Rámce Windows SDI a MDI aplikacemi

Pro aplikace SDI je jedno okno rámce odvozené od třídy [CFrameWnd](../mfc/reference/cframewnd-class.md). Toto okno je hlavní okno rámce a okna rámce dokumentu. Pro aplikace MDI, hlavní okno rámce je odvozena od třídy [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), a rámečkem v dokumentu, které jsou podřízených oken MDI, jsou odvozeny z třídy [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md).

## <a name="use-the-frame-window-class-or-derive-from-it"></a>Použití třídy oken s rámečkem nebo z něj odvodit

Tyto třídy poskytují většinu oken s rámečkem funkcí, které potřebujete pro své aplikace. Za normálních okolností výchozí chování a vzhled, které poskytují a bude vyhovovat vašim potřebám. Pokud potřebujete další funkce, jsou odvozeny z těchto tříd.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Třídy oken s rámečkem vytvořené průvodcem aplikací](../mfc/frame-window-classes-created-by-the-application-wizard.md)

- [Styly oken s rámečkem](../mfc/frame-window-styles-cpp.md)

- [Změna stylů okna vytvořeného rozhraním MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>Viz také:

[Okna s rámečkem](../mfc/frame-windows.md)
