---
title: Styly číselníků | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 223b7e0875a5382edf5f4d350c9343d117768c41
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953775"
---
# <a name="spin-button-styles"></a>Styly číselníků
Mnoho z nastavení typu číselník ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)) jsou řízeny stylů. Můžete nastavit následující styly pomocí **vlastnosti** okno v editoru dialogového okna.  
  
-   **Orientace** svislé nebo vodorovné. Ovládací prvky orientaci tlačítek se šipkami. Styl UDS_HORZ přidružené.  
  
-   **Zarovnání** mezi odpojit, doleva nebo doprava. Určuje umístění číselníku. Levá a pravá pozice číselníku vedle kamarád okna. Šířka okna kamarád dojde k omezení pro přizpůsobení číselníku. Styly UDS_ALIGNLEFT a UDS_ALIGNRIGHT přidružené.  
  
-   **Automaticky kamarád** automaticky vybere předchozího okna v pořadí vykreslování jako kamarád okna na tlačítko otočení. V šablony dialogového okna je to řídit, která předchází číselníku v pořadí. Styl UDS_AUTOBUDDY přidružené.  
  
-   **Nastavit celé číslo kamarád** způsobí, že ovládací prvek typu číselník zvýší a sníží titulek okna kamarád jako aktuální pozici změny. Styl UDS_SETBUDDYINT přidružené.  
  
-   **Žádné tisíc** nevkládá tisíců oddělovače v hodnotě v záhlaví okna kamarád. Styl UDS_NOTHOUSANDS přidružené.  
  
    > [!NOTE]
    >  Nastavte tento styl, pokud chcete používat k získání celočíselnou hodnotu z ovládacího prvku kamarád výměna dialogových dat (DDX). `DDX_Text` nepřijímá embedded oddělovače tisíců.  
  
-   **Zabalení** způsobí, že pozice "zabalit", protože tato hodnota se zvýšena nebo snížena mimo rozsah ovládacího prvku. Styl UDS_WRAP přidružené.  
  
-   **Klávesy se šipkami** způsobí, že číselníku zvýší nebo sníží pozici při stisknutí klávesy šipka nahoru a Šipka dolů. Styl UDS_ARROWKEYS přidružené.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

