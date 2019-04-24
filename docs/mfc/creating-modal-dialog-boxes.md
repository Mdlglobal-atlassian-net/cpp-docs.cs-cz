---
title: Vytváření modálních dialogových oken
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: 5de6eeb616f32c7b8829d827988a972e41658530
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174091"
---
# <a name="creating-modal-dialog-boxes"></a>Vytváření modálních dialogových oken

Chcete-li vytvoření modálního dialogového okna, zavolejte buď dvě veřejné konstruktory deklarované v [CDialog](../mfc/reference/cdialog-class.md). V dalším kroku volání objektu dialogového okna [DoModal](../mfc/reference/cdialog-class.md#domodal) členské funkce k zobrazení dialogového okna a spravovat interakce s ním, dokud uživatel zvolí OK nebo zrušit. Tuto správu `DoModal` díky modální dialogové okno. Pro modální dialogová okna `DoModal` načte prostředku dialogového okna.

## <a name="see-also"></a>Viz také:

[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)
