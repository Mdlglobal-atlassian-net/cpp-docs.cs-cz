---
title: Vytváření modálních dialogových oken | Microsoft Docs
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
ms.openlocfilehash: 2a8bc947dbaf9cecc680f3cdbd8e6b429d2bcd5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="creating-modal-dialog-boxes"></a>Vytváření modálních dialogových oken
Modální dialogové okno vytvořit, volání buď dvě veřejné konstruktory deklarované v [CDialog](../mfc/reference/cdialog-class.md). Pak zavolejte objektu dialogového okna [DoModal](../mfc/reference/cdialog-class.md#domodal) – členská funkce lze zobrazit dialogové okno a spravovat interakci s ním, dokud uživatel vybere OK nebo zrušit. Tato správu `DoModal` je díky modální dialogové okno. Pro modálních dialogových oken `DoModal` načte prostředku dialogového okna.  
  
## <a name="see-also"></a>Viz také  
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

