---
title: Vytváření modálních dialogových oken | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3fcc449a376091c07a7fb26b81fe19752bc3bcd6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376641"
---
# <a name="creating-modal-dialog-boxes"></a>Vytváření modálních dialogových oken

Chcete-li vytvoření modálního dialogového okna, zavolejte buď dvě veřejné konstruktory deklarované v [CDialog](../mfc/reference/cdialog-class.md). V dalším kroku volání objektu dialogového okna [DoModal](../mfc/reference/cdialog-class.md#domodal) členské funkce k zobrazení dialogového okna a spravovat interakce s ním, dokud uživatel zvolí OK nebo zrušit. Tuto správu `DoModal` díky modální dialogové okno. Pro modální dialogová okna `DoModal` načte prostředku dialogového okna.

## <a name="see-also"></a>Viz také

[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

