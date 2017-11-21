---
title: "Styly číselníků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 92881b4c6bab1deaf35ba11e10dbea318194bd05
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="spin-button-styles"></a>Styly číselníků
Mnoho z nastavení typu číselník ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)) jsou řízeny stylů. Můžete nastavit následující styly pomocí **vlastnosti** okno v editoru dialogového okna.  
  
-   **Orientace** svislé nebo vodorovné. Ovládací prvky orientaci tlačítek se šipkami. Přidružené `UDS_HORZ` stylu.  
  
-   **Zarovnání** mezi odpojit, doleva nebo doprava. Určuje umístění číselníku. Levá a pravá pozice číselníku vedle kamarád okna. Šířka okna kamarád dojde k omezení pro přizpůsobení číselníku. Přidružené `UDS_ALIGNLEFT` a `UDS_ALIGNRIGHT` styly.  
  
-   **Automaticky kamarád** automaticky vybere předchozího okna v pořadí vykreslování jako kamarád okna na tlačítko otočení. V šablony dialogového okna je to řídit, která předchází číselníku v pořadí. Přidružené `UDS_AUTOBUDDY` stylu.  
  
-   **Nastavit celé číslo kamarád** způsobí, že ovládací prvek typu číselník zvýší a sníží titulek okna kamarád jako aktuální pozici změny. Přidružené `UDS_SETBUDDYINT` stylu.  
  
-   **Žádné tisíc** nevkládá tisíců oddělovače v hodnotě v záhlaví okna kamarád. Přidružené `UDS_NOTHOUSANDS` stylu.  
  
    > [!NOTE]
    >  Nastavte tento styl, pokud chcete používat k získání celočíselnou hodnotu z ovládacího prvku kamarád výměna dialogových dat (DDX). `DDX_Text`nepřijímá embedded oddělovače tisíců.  
  
-   **Zabalení** způsobí, že pozice "zabalit", protože tato hodnota se zvýšena nebo snížena mimo rozsah ovládacího prvku. Přidružené `UDS_WRAP` stylu.  
  
-   **Klávesy se šipkami** způsobí, že číselníku zvýší nebo sníží pozici při stisknutí klávesy šipka nahoru a Šipka dolů. Přidružené `UDS_ARROWKEYS` stylu.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

