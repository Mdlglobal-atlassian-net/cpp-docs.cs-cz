---
title: Vytváření modálních dialogových oken
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: eb9aab7e8579fbbbfdf5d0f2dca9b6e6abea0066
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657336"
---
# <a name="creating-modal-dialog-boxes"></a>Vytváření modálních dialogových oken

Chcete-li vytvoření modálního dialogového okna, zavolejte buď dvě veřejné konstruktory deklarované v [CDialog](../mfc/reference/cdialog-class.md). V dalším kroku volání objektu dialogového okna [DoModal](../mfc/reference/cdialog-class.md#domodal) členské funkce k zobrazení dialogového okna a spravovat interakce s ním, dokud uživatel zvolí OK nebo zrušit. Tuto správu `DoModal` díky modální dialogové okno. Pro modální dialogová okna `DoModal` načte prostředku dialogového okna.

## <a name="see-also"></a>Viz také

[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

