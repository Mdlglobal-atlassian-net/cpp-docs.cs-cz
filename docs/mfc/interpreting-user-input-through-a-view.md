---
title: Interpretace vstupu uživatele prostřednictvím zobrazení
ms.date: 11/04/2016
helpviewer_keywords:
- interpreting user input through views [MFC]
- views [MFC], user interface and input
- input [MFC], view class [MFC]
- CView class [MFC], interpreting user input
- user input [MFC], interpreting through view class [MFC]
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
ms.openlocfilehash: fe64f7c499b4a7c93f628fa0dff0855c379cbd58
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552565"
---
# <a name="interpreting-user-input-through-a-view"></a>Interpretace vstupu uživatele prostřednictvím zobrazení

Další členské funkce zobrazení zpracování a interpretovat všechny uživatelský vstup. Obslužná rutina zprávy členské funkce se obvykle definují ve třídě zobrazení zpracování:

- Windows [zprávy](../mfc/messages.md) generovaných událostmi myši a klávesnice.

- [Příkazy](../mfc/user-interface-objects-and-command-ids.md) z nabídky, tlačítek panelu nástrojů a přístupové klávesy.

Tyto členské funkce obslužná rutina zprávy interpretovat takto vstupu dat, výběr nebo úpravy, včetně přesun dat do a ze schránky:

- Pohyb myši a klikne na tlačítko, přetáhne a poklikáním

- Úhozy na klávesnici

- Příkazy nabídky

Zprávy, které Windows zobrazení popisovačů závisí na potřebách vaší aplikace.

[Zpracování a mapování témata zpráv](../mfc/message-handling-and-mapping.md) vysvětluje, jak přiřadit položky nabídky a dalších objektů uživatelského rozhraní pro příkazy a o tom, k vytvoření vazby příkazu k funkcím obslužných rutin. [Zpracování a mapování témata zpráv](../mfc/message-handling-and-mapping.md) také vysvětluje, jak MFC směruje příkazy a odešle standardní zprávy Windows na objekty, které obsahují obslužné rutiny pro ně.

Vaše aplikace například může být nutné implementovat přímým přístupem myši kreslení v zobrazení. Ukázky Scribble ukazuje, jak zpracovávat zprávy WM_LBUTTONDOWN wm_mousemove a a WM_LBUTTONUP v uvedeném pořadí chcete začít, pokračovat a ukončit vykreslování úsek čáry. Na druhé straně můžete někdy potřebovat k interpretaci kliknutí myší v zobrazení jako výběr. Vaše zobrazení `OnLButtonDown` funkci obslužné rutiny by určit, zda byl uživatel kreslení nebo výběru. Pokud vyberete, obslužnou rutinu by určit, zda byl kliknutí v mezích některý objekt v zobrazení a pokud ano, změnit zobrazení na Zobrazit jako vybraný objekt.

Zobrazení může také zpracovávat určité příkazy nabídek, jako jsou ty z nabídky Úpravy na vyjmutí, kopírování, vložení nebo odstranění vybraných dat pomocí schránky. Tyto rutiny by volat některý člen schránky související funkce třídy `CWnd` přenést položka vybraná data do nebo ze schránky.

## <a name="see-also"></a>Viz také

[Použití zobrazení](../mfc/using-views.md)

