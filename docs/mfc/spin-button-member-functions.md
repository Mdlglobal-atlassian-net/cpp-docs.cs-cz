---
title: "Členské funkce číselníku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- spin button control, methods
- CSpinButtonCtrl class [MFC], methods
ms.assetid: a08a26fd-b803-4cbe-a509-395fa357d057
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6f0abfd5803ea4b4d4b4478104790e0f56e5afc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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

