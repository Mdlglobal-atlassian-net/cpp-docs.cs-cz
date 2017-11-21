---
title: "Vytváření modálních dialogových oken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 662455a3ad0c45b287f485e3b87cc5437343bffb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-modal-dialog-boxes"></a>Vytváření modálních dialogových oken
Modální dialogové okno vytvořit, volání buď dvě veřejné konstruktory deklarované v [CDialog](../mfc/reference/cdialog-class.md). Pak zavolejte objektu dialogového okna [DoModal](../mfc/reference/cdialog-class.md#domodal) – členská funkce lze zobrazit dialogové okno a spravovat interakci s ním, dokud uživatel vybere OK nebo zrušit. Tato správu `DoModal` je díky modální dialogové okno. Pro modálních dialogových oken `DoModal` načte prostředku dialogového okna.  
  
## <a name="see-also"></a>Viz také  
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)

