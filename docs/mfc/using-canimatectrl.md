---
title: Používání atributu CAnimateCtrl
ms.date: 11/04/2016
f1_keywords:
- CAnimateCtrl
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
ms.openlocfilehash: 00b285ba2ec1bcd7fa524d5e20190f806819947f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449218"
---
# <a name="using-canimatectrl"></a>Používání atributu CAnimateCtrl

Ovládacího prvku animace reprezentovaný třídou [atributu CAnimateCtrl](../mfc/reference/canimatectrl-class.md), je okno, které zobrazuje klipu ve formátu zvuku videa prokládané (AVI) – standard video nebo Zvuk formátu Windows. Klip AVI je řada rastrového obrázku rámce, jako jsou videa.

Protože vaše vlákno pokračuje v provádění, když klip AVI se zobrazí, je jedno společné použití ovládacího prvku animace indikovat aktivitu systému během operace s delším průběhem. Například dialogové okno hledání Windows zobrazí přesunutí Lupa jako systém vyhledá soubor.

Ovládací prvky animace lze pouze přehrávání jednoduché AVI a nepodporují zvuku. (Úplný seznam omezení, najdete v části [atributu CAnimateCtrl](../mfc/reference/canimatectrl-class.md).) Vzhledem k tomu, že jsou přísně omezené možnosti ovládacího prvku animace a můžou se změnit, měli byste použít alternativu, jako je například ovládací prvek MCIWnd potřebujete ovládacího prvku k poskytování multimédií přehrávání a/nebo možnosti nahrávání. Další informace o ovládacím prvku MCIWnd multimediální dokumentaci.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Použití ovládacího prvku animace](../mfc/using-an-animation-control.md)

- [Oznámení zaslaná z ovládacích prvků animace](../mfc/notifications-sent-by-animation-controls.md)

## <a name="see-also"></a>Viz také

[Ovládací prvky](../mfc/controls-mfc.md)

