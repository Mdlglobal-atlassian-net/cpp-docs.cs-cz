---
title: Portrét architektury dokumentů a zobrazení
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], views
- multiple views [MFC], updating from document
- document/view architecture [MFC]
- views [MFC], and user input
- documents [MFC], accessing data from view
- views [MFC], updating
- input [MFC], view class
- documents [MFC], multiple views
- document/view architecture [MFC], accessing data from view
- document/view architecture [MFC], about document/view architecture
- views [MFC], accessing document data from
ms.assetid: 4e7f65dc-b166-45d8-bcd5-9bb0d399b946
ms.openlocfilehash: a4d89189b5389685be6b69c8502ffedb8aa731e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567099"
---
# <a name="a-portrait-of-the-documentview-architecture"></a>Portrét architektury dokument/zobrazení

V typické aplikaci knihovny MFC jsou párovány dokumentů a zobrazení. Data se ukládají v dokumentu, ale zobrazení obsahuje privilegovaný přístup k datům. Oddělení dokumentu ze zobrazení odděluje úložiště a údržby dat od jeho zobrazení.

## <a name="gaining-access-to-document-data-from-the-view"></a>Získání přístupu k datům ze zobrazení dokumentů

Zobrazení má přístup k jeho dokumentu dat buď pomocí [GetDocument](../mfc/reference/cview-class.md#getdocument) funkci, která vrací ukazatel na dokument nebo tím, že zobrazení třídy jazyka C++ `friend` třídy dokumentu. Zobrazení pak používá jeho přístup k datům na získání dat, když je připravený k vykreslení nebo s ním jinak pracovat.

Například ze zobrazení [OnDraw](../mfc/reference/cview-class.md#ondraw) členská funkce používá zobrazení `GetDocument` získat ukazatele dokumentu. Potom použije tento ukazatel pro přístup k `CString` datový člen v dokumentu. Řetězec, který se předá zobrazení `TextOut` funkce. Kód v tomto příkladu najdete v tématu [kreslení v zobrazení](../mfc/drawing-in-a-view.md).

## <a name="user-input-to-the-view"></a>Uživatelský vstup do zobrazení

Zobrazení mohou také interpretovat kliknutí myší v rámci samotného jako výběr nebo upravovat data. Podobně se může interpretovat stisknutí kláves jako vstupní data nebo úpravy. Předpokládejme, že uživatel zadá řetězec v zobrazení, která spravuje text. Toto zobrazení získá ukazatel na dokument a používá ukazatel k předání nová data v dokumentu, který ukládá některé datové struktury.

## <a name="updating-multiple-views-of-the-same-document"></a>Aktualizuje se několik zobrazení stejné dokumentu

V aplikaci s více zobrazení stejného dokumentu, jako je například okno s rozdělovačem v textovém editoru – zobrazení nejprve předává nová data do dokumentu. Potom volá dokumentu [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) členská funkce, který informuje všechna zobrazení dokumentu, který se aktualizují samy, odráží nová data. Provádí synchronizaci zobrazení.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Výhody architektury dokument/zobrazení](../mfc/advantages-of-the-document-view-architecture.md)

- [Alternativy k architektuře dokument/zobrazení](../mfc/alternatives-to-the-document-view-architecture.md)

## <a name="see-also"></a>Viz také

[Document/View – architektura](../mfc/document-view-architecture.md)

