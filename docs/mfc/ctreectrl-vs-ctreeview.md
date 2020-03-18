---
title: CTreeCtrl vs. CTreeView
ms.date: 11/04/2016
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
ms.openlocfilehash: 7c78dfa9920c913fdbedb009c5a6f275a3e3e273
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445227"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl vs. CTreeView

Knihovna MFC poskytuje dvě třídy, které zapouzdřují ovládací prvky stromu: [CTreeCtrl](../mfc/reference/ctreectrl-class.md) a [CTreeView –](../mfc/reference/ctreeview-class.md). Každá třída je užitečná v různých situacích.

Použijte `CTreeCtrl`, když potřebujete ovládací prvek jednoduchého podřízeného okna; například v dialogovém okně. Byste obzvláště chtěli použít `CTreeCtrl`, pokud budou v okně jiné podřízené ovládací prvky, jako v typickém dialogovém okně.

Použijte `CTreeView`, pokud chcete, aby měl ovládací prvek stromu fungovat jako okno zobrazení v architektuře document/view, stejně jako ovládací prvek stromu. `CTreeView` bude zabírat celou klientskou oblast okna rámce nebo okna s rozdělovačem. Velikost se automaticky změní při změně velikosti nadřazeného okna a může zpracovávat příkazové zprávy z nabídek, kláves akcelerátorů a panelů nástrojů. Vzhledem k tomu, že stromová struktura obsahuje data potřebná pro zobrazení stromu, odpovídající objekt dokumentu nemusí být složitý – v šabloně dokumentu můžete dokonce použít [objektu CDocument](../mfc/reference/cdocument-class.md) jako typ dokumentu.

## <a name="see-also"></a>Viz také

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
