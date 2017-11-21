---
title: "Přístup k Embedded měsíce v ovládacím prvku Kalendář | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DateTimePicker control [MFC], accessing month calendar
- CDateTimeCtrl class [MFC], accessing embedded control
- month calendar controls [MFC], embedded in date/time picker
- CMonthCalCtrl class [MFC], changing the font
- month calendar controls [MFC], changing the font
- DateTimePicker control [MFC]
ms.assetid: 355e97ed-cf81-4df3-a2f8-9ddbbde93227
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6c39d2ae9341a245c66d5a91b5c98cc43c682b39
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="accessing-the-embedded-month-calendar-control"></a>Přístup k vloženému ovládacímu prvku měsíční kalendář
Objekt ovládacího prvku Kalendář embedded měsíc je přístupná z `CDateTimeCtrl` objekt s volání [GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl) – členská funkce.  
  
> [!NOTE]
>  Ovládací prvek embedded měsíční kalendář se používá pouze v případě, že nemá prvku pro výběr data a času **DTS_UPDOWN** styl sady.  
  
 To je užitečné, pokud chcete změnit určité atributy dříve, než se zobrazí vloženému ovládacímu prvku. K tomu, zpracování **dtn_dropdown –** oznámení, načíst ovládací prvek měsíční kalendář (pomocí [CDateTimeCtrl::GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)) a proveďte úpravy. Ovládací prvek měsíční kalendář bohužel není trvalý.  
  
 Jinými slovy, když si uživatel vyžádá zobrazení ovládací prvek měsíční kalendář, ovládacího prvku Kalendář nového měsíce se vytvoří (před **dtn_dropdown –** oznámení). Zničení ovládacího prvku (po **dtn_closeup –** oznámení) při uživatelem zamítnuta. To znamená, že libovolné atributy, které můžete upravit, než se zobrazí vloženému ovládacímu prvku, jsou ztraceny, když se zruší vloženému ovládacímu prvku.  
  
 Následující příklad ukazuje, tento postup, obslužné rutiny pro použití **dtn_dropdown –** oznámení. Kód změní barvu pozadí ovládací prvek měsíční kalendář, pomocí volání [SetMonthCalColor](../mfc/reference/cdatetimectrl-class.md#setmonthcalcolor), šedou barvu. Kód je následující:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]  
  
 Jak jsme uvedli dříve, se ztratí, se dvěma výjimkami, všechny změny vlastností ovládací prvek měsíční kalendář, když se zruší vloženému ovládacímu prvku. První výjimka barvy ovládací prvek měsíční kalendář má již popsány. Druhou výjimkou je písmo použité ovládací prvek měsíční kalendář. Můžete upravit výchozí písmo tím, že zavoláte na [CDateTimeCtrl::SetMonthCalFont](../mfc/reference/cdatetimectrl-class.md#setmonthcalfont), předávání popisovač existující písma. Následující příklad (kde `m_dtPicker` je datum a čas objekt ovládacího prvku) ukazuje jedna z možných metod:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]  
  
 Jakmile změníte písmo, pomocí volání `CDateTimeCtrl::SetMonthCalFont`, nové písmo uložena a následně použít při příštím měsíční kalendář se mají zobrazit.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

