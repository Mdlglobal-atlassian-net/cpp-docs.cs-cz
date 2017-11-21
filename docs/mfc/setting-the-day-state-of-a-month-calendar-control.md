---
title: "Nastavení stavu dne v měsíci v ovládacím prvku Kalendář | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MCN_GETDAYSTATE
dev_langs: C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7b0949cd28683ff577c29ade459b89185f020377
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>Nastavení stavu dne v ovládacím prvku měsíční kalendář
Jeden z atributů prvku měsíční kalendář je možnost ukládat informace, označuje jako stavu dne v ovládacím prvku pro každý den v měsíci. Tyto informace slouží k zdůraznil určitá data pro aktuálně zobrazený měsíc.  
  
> [!NOTE]
>  `CMonthCalCtrl` Objekt musí mít **MCS_DAYSTATE** styl zobrazíte informace o stavu den.  
  
 Informace o stavu den je vyjádřený jako typ dat 32-bit **MONTHDAYSTATE**. Každý bit ve **MONTHDAYSTATE** bitová pole (1 až 31) představuje stav den v měsíci. Pokud je bit na, zobrazí se odpovídající den v bold; v opačném případě se bude zobrazovat s žádné zvýraznění.  
  
 Existují dvě metody pro nastavení stavu dne v ovládacím prvku měsíční kalendář: explicitně pomocí volání [CMonthCalCtrl::SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) nebo zpracování **mcn_getdaystate –** oznámení.  
  
## <a name="handling-the-mcngetdaystate-notification-message"></a>Zpracování zpráv mcn_getdaystate – oznámení  
 **Mcn_getdaystate –** zprávy pomocí ovládacího prvku určit, jak mají být zobrazeny dny v rámci viditelné měsíců.  
  
> [!NOTE]
>  Protože ovládací prvek ukládá do mezipaměti předešlých a následných měsíců, která z hlediska viditelné měsíc, zobrazí se toto oznámení pokaždé, když je vybrán na nový měsíc.  
  
 Správně zpracovat tuto zprávu, je třeba určit, kolik měsíců informace o stavu den se vyžaduje pro, inicializovat pole **MONTHDAYSTATE** struktury s správné hodnoty a inicializaci související struktura člena s novými informacemi. Následující postup, s podrobnostmi o potřebné kroky, předpokládá, že máte `CMonthCalCtrl` objektu s názvem `m_monthcal` a pole **MONTHDAYSTATE** objekty, `mdState`.  
  
#### <a name="to-handle-the-mcngetdaystate-notification-message"></a>Zpracování zpráv mcn_getdaystate – oznámení  
  
1.  Pomocí okna vlastností, přidejte obslužnou rutinu oznámení pro **mcn_getdaystate –** zprávy do `m_monthcal` objektu (najdete v části [mapování zpráv do funkcí](../mfc/reference/mapping-messages-to-functions.md)).  
  
2.  V těle obslužná rutina přidejte následující kód:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]  
  
     V příkladu převede `pNMHDR` ukazatel na správný typ., pak určuje, kolik měsíců informace se vyžadují (`pDayState->cDayState`). Pro každý měsíc, aktuální bitfield (`pDayState->prgDayState[i]`) je inicializováno nula a pak potřebné data jsou nastavit (v tomto případě 15. dne v měsíci).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

