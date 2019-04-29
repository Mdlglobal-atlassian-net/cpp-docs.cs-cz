---
title: Třídy oken s rámečkem (Windows)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], reference
ms.assetid: 6342ec5f-f922-4da8-a78e-2f5f994c7142
ms.openlocfilehash: 3e56bd0f449992118db75a44c39b6e0e15cb0d86
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392790"
---
# <a name="frame-window-classes-windows"></a>Třídy oken s rámečkem (Windows)

Okna s rámečkem jsou windows, která ohraničují aplikace nebo součást aplikace. Okna s rámečkem obvykle obsahují jiných oknech, jako je například zobrazení, panely nástrojů a stavové řádky. V případě třídy `CMDIFrameWnd`, mohou obsahovat `CMDIChildWnd` nepřímo objekty.

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
Základní třída pro okna hlavního rámce aplikace SDI. Také základní třída pro všechny ostatní třídy oken s rámečkem.

[CMDIFrameWnd –](../mfc/reference/cmdiframewnd-class.md)<br/>
Základní třída pro aplikace MDI hlavní okno rámce.

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
Základní třída pro aplikace MDI oken s rámečkem v dokumentu.

[Cminiframewnd –](../mfc/reference/cminiframewnd-class.md)<br/>
Okno rámce poloviční výšky obvykle viděné okolo plovoucích panelů nástrojů.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Pokud dokument na serveru je upravována v místě, poskytuje okno rámce pro zobrazení.

## <a name="related-class"></a>Související třídy

Třída `CMenu` poskytuje rozhraní, pomocí kterého je možné přistupovat k vaší aplikaci nabídky. Je užitečné pro manipulaci s nabídky dynamicky za běhu; například při přidání nebo odstranění položek nabídky podle kontextu. I když nabídky se nejčastěji používají s oken s rámečkem, můžete také používají se dialogová okna a dalších oknech nonchild.

[Cmenu –](../mfc/reference/cmenu-class.md)<br/>
Zapouzdřuje `HMENU` popisovač na řádku nabídek a místní nabídky aplikace.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../mfc/class-library-overview.md)
