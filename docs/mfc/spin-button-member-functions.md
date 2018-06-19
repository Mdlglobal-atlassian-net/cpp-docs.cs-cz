---
title: Členské funkce číselníku | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- spin button control, methods
- CSpinButtonCtrl class [MFC], methods
ms.assetid: a08a26fd-b803-4cbe-a509-395fa357d057
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 524863b816c62903cb610b57a6e3275bcdf6a3d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381248"
---
# <a name="spin-button-member-functions"></a>Členské funkce číselníku
Nejsou k dispozici pro ovládací prvek typu číselník několik členské funkce ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)). Chcete-li změnit následující atributy číselníku pomocí těchto funkcí.  
  
-   **Akcelerace** můžete upravit rychlost, jakou pozici změní, když uživatel obsahuje šipku dolů. Chcete-li pracovat s akcelerace, použijte [SetAccel](../mfc/reference/cspinbuttonctrl-class.md#setaccel) a [GetAccel](../mfc/reference/cspinbuttonctrl-class.md#getaccel) členské funkce.  
  
-   **Základní** základní (10 nebo 16) slouží k zobrazení umístění v záhlaví okna kamarád, můžete změnit. Chcete-li pracovat s základní, použijte [getbase –](../mfc/reference/cspinbuttonctrl-class.md#getbase) a [SetBase](../mfc/reference/cspinbuttonctrl-class.md#setbase) členské funkce.  
  
-   **Kamarád okno** dynamicky můžete nastavit kamarád okna. Dotaz nebo změnit, který ovládací prvek je okno kamarád, použijte [GetBuddy](../mfc/reference/cspinbuttonctrl-class.md#getbuddy) a [SetBuddy](../mfc/reference/cspinbuttonctrl-class.md#setbuddy) členské funkce.  
  
-   **Pozice** můžete dotazovat a změnit umístění. Chcete-li pracovat přímo s pozice, použijte [GetPos](../mfc/reference/cspinbuttonctrl-class.md#getpos) a [SetPos](../mfc/reference/cspinbuttonctrl-class.md#setpos) členské funkce. Vzhledem k tomu mohlo dojít ke změně titulek přidružený ovládací prvek (například v případě, že kamarád je ovládací prvek upravit), `GetPos` načte aktuální záhlaví a odpovídajícím způsobem upraví pozici.  
  
-   **Rozsah** můžete změnit na maximální a minimální pozici pro číselníku. Ve výchozím nastavení je maximální nastavena na hodnotu 0 a minimální je nastavena na hodnotu 100. Vzhledem k tomu, že výchozí maximum je menší než minimální výchozí, je counter-intuitive akce tlačítek se šipkami. Obvykle bude nastavena pomocí rozsahu [SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) – členská funkce. K dotazování použití rozsah [getrange –](../mfc/reference/cspinbuttonctrl-class.md#getrange).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

