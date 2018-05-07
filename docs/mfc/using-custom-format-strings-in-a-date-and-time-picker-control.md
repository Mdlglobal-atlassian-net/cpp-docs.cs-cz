---
title: Použití řetězců vlastního formátu v výběr data a času řízení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CDateTimeCtrl class [MFC], display styles
- DateTimePicker control [MFC], display styles
- DateTimePicker control [MFC]
ms.assetid: 7d577f03-6ca0-4597-9093-50b78f304719
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2b365439f1681cf72bd58218ea4f55fbb2f44c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-custom-format-strings-in-a-date-and-time-picker-control"></a>Použití řetězců vlastního formátu v ovládacím prvku pro výběr data a času
Ve výchozím nastavení ovládací prvky pro výběr data a času poskytují že tři typy (každý formát odpovídající jedinečný styl) formátu pro zobrazení aktuálního data a času:  
  
-   **DTS_LONGDATEFORMAT** zobrazí datum v dlouho formátu, který vytvořil výstup jako "Středa 3 leden 2000".  
  
-   **DTS_SHORTDATEFORMAT** zobrazí datum v krátké formátu, který vytvořil výstup jako "1/3/00".  
  
-   **DTS_TIMEFORMAT** zobrazí čas v dlouho formátu, který vytvořil výstup jako "5:31:42 odp.".  
  
 Ale můžete přizpůsobit vzhled data a času pomocí vlastní řetězec formátu. Tento vlastní řetězec se skládá z existující formát znaky, znaky nonformat nebo obojí. Po vlastním řetězcem, ujistěte se, volání [CDateTimeCtrl::SetFormat](../mfc/reference/cdatetimectrl-class.md#setformat) předávání v vlastní řetězec. Prvku pro výběr data a času se potom zobrazí aktuální hodnotu pomocí vlastní formátovací řetězec.  
  
 Následující příklad kódu (kde `m_dtPicker` je `CDateTimeCtrl` objektu) ukazuje jedním z možných řešení:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#7](../mfc/codesnippet/cpp/using-custom-format-strings-in-a-date-and-time-picker-control_1.cpp)]  
  
 Kromě řetězců vlastního formátu také prvky pro výběr data a času podporu [pole zpětného volání](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

