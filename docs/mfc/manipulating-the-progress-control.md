---
title: Manipulace s ovládacím prvkem průběh | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CProgressCtrl class [MFC], working with
- progress controls [MFC], manipulating
- CProgressCtrl class [MFC], manipulating
- controlling progress controls [MFC]
- CProgressCtrl class [MFC], using
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 415061306c5e743b9ed95ee5c7105133d2e4d340
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="manipulating-the-progress-control"></a>Manipulace s ovládacím prvkem průběh
Existují tři způsoby, jak změnit aktuální pozici ovládací prvek průběh ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)).  
  
-   Pozice může změnit velikost přednastavené přírůstku.  
  
-   Pozice může změnit libovolné množství.  
  
-   Pozice můžete změnit na určitou hodnotu.  
  
### <a name="to-change-the-position-by-a-preset-amount"></a>Chcete-li změnit pozice přednastavené vzdálenost  
  
1.  Použití [SetStep](../mfc/reference/cprogressctrl-class.md#setstep) – členská funkce nastavit velikost přírůstku. Ve výchozím nastavení je tato hodnota 10. Tato hodnota se obvykle nastavena jako jeden z počátečního nastavení pro ovládací prvek. Hodnota kroku může být záporné.  
  
2.  Použití [StepIt](../mfc/reference/cprogressctrl-class.md#stepit) – členská funkce se zvýší pozici. To způsobí, že k překreslit ovládacího prvku.  
  
    > [!NOTE]
    >  `StepIt` způsobí, že pozice zabalit. Například zadaný rozsah 1 -100, krok 20 a pozice 90 `StepIt` nastaví pozici na hodnotu 10.  
  
### <a name="to-change-the-position-by-an-arbitrary-amount"></a>Chcete-li změnit umístění pomocí libovolné množství  
  
1.  Použití [OffsetPos](../mfc/reference/cprogressctrl-class.md#offsetpos) – členská funkce chcete změnit umístění. `OffsetPos` přijme záporné hodnoty.  
  
    > [!NOTE]
    >  `OffsetPos`, na rozdíl od `StepIt`, nebude zabalení pozici. Nové pozice se upraví zůstat v rozsahu.  
  
### <a name="to-change-the-position-to-a-specific-value"></a>Chcete-li změnit umístění na určitou hodnotu  
  
1.  Použití [SetPos](../mfc/reference/cprogressctrl-class.md#setpos) – členská funkce nastavíte umístění na určitou hodnotu. V případě potřeby se upraví nové pozice musí být v rozsahu.  
  
 Ovládací prvek průběh se obvykle používá výhradně pro výstup. Aktuální pozice bez zadání nové hodnoty, použijte [GetPos](../mfc/reference/cprogressctrl-class.md#getpos).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CProgressCtrl](../mfc/using-cprogressctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

