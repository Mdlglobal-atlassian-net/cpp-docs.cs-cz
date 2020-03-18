---
title: Používání atributu CAnimateCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
ms.openlocfilehash: 79c1a0111317514ef6fd68acd0c6a2ebdccc3ba4
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447101"
---
# <a name="using-canimatectrl"></a>Používání atributu CAnimateCtrl

Ovládací prvek animace reprezentovaný třídou [atributu CAnimateCtrl](../mfc/reference/canimatectrl-class.md)je okno, které zobrazuje klip ve formátu AVI (audio video provisioned), což je standardní formát videa nebo zvuku ve Windows. Klip AVI je série rastrových snímků, jako je třeba film.

Vzhledem k tomu, že vaše vlákno pokračuje v době, kdy se zobrazuje klip AVI, je jedno běžné použití pro ovládací prvek animace označovat aktivitu systému během zdlouhavé operace. Například v dialogovém okně Najít v systému Windows se při hledání souboru zobrazí zvětšovací Lupa.

Ovládací prvky animace mohou přehrávat pouze jednoduché klipy AVI a nepodporují zvuk. Úplný seznam omezení najdete v tématu [atributu CAnimateCtrl](../mfc/reference/canimatectrl-class.md).) Vzhledem k tomu, že možnosti ovládacího prvku animace jsou vážně omezené a mohou se změnit, měli byste použít alternativu jako ovládací prvek MCIWnd, pokud potřebujete ovládací prvek pro poskytování multimediálního přehrávání a/nebo nahrávání možností. Další informace o ovládacím prvku MCIWnd naleznete v dokumentaci k multimédiím.

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Použití ovládacího prvku animace](../mfc/using-an-animation-control.md)

- [Oznámení zaslaná z ovládacích prvků animace](../mfc/notifications-sent-by-animation-controls.md)

## <a name="see-also"></a>Viz také

[Ovládací prvky](../mfc/controls-mfc.md)
