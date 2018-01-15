---
title: "Implementace pracovních oblastí v ovládacích prvcích seznam | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cefb8007fd9b73dda4c0e8a99e9ae9daa1bfcc34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-working-areas-in-list-controls"></a>Implementace pracovních oblastí v ovládacích prvcích seznam
Ve výchozím nastavení uspořádá ovládací prvek seznamu všechny položky způsobem standardní mřížky. Ale je podporované jinou metodu, pracovních oblastí, které jsou uspořádány položky seznamu obdélníková skupiny. Obrázek ovládacího prvku seznam, který implementuje pracovní oblasti najdete pomocí zobrazení seznamu ovládacích prvků ve Windows SDK.  
  
> [!NOTE]
>  Pracovní oblasti jsou viditelné pouze v případě, že ovládacího prvku seznam je v režimu malé ikony nebo ikonu. Všechny aktuální pracovní oblasti se ale zachovají, pokud zobrazení je přepnuta do režimu sestavu nebo seznamu.  
  
 Pracovní oblasti slouží k zobrazení prázdný ohraničení (v levé horní nebo napravo od položky) nebo způsobit vodorovného posuvníku, který se má zobrazit při za normálních okolností by existovat jeden. Další běžné využití je vytvoření více pracovní oblasti, ke kterým můžete přesunout položky nebo vyřadit. Pomocí této metody můžete vytvořit oblasti v rámci jednoho zobrazení, které mají různé významy. Uživatel pak může kategorizace položek tím, že je v jiné oblasti. Příkladem může být zobrazení systému souborů, který má oblast pro čtení a zápis souborů a jiné oblasti pro soubory jen pro čtení. Pokud soubor položky byly přesunuty do oblasti jen pro čtení, by automaticky stane jen pro čtení. Přesun souboru z oblasti jen pro čtení do oblasti pro čtení a zápis by zkontrolujte soubor pro čtení a zápis.  
  
 `CListCtrl`poskytuje několik členské funkce pro vytváření a správa pracovních prostorech v ovládacím prvku vašeho seznamu. [GetWorkAreas](../mfc/reference/clistctrl-class.md#getworkareas) a [SetWorkAreas](../mfc/reference/clistctrl-class.md#setworkareas) načíst a nastavit pole `CRect` objekty (nebo `RECT` struktury), který uložit aktuální implementace pracovní oblasti pro vaše ovládací prvek seznamu. Kromě toho [GetNumberOfWorkAreas](../mfc/reference/clistctrl-class.md#getnumberofworkareas) načte aktuální počet pracovní oblasti pro vaše ovládací prvek seznamu (ve výchozím nastavení, nula).  
  
## <a name="items-and-working-areas"></a>Položek a pracovní oblasti  
 Když je vytvořen pracovní oblasti, položky, které jsou v pracovní oblasti se stanou členy ho. Podobně pokud položku přesunete do pracovní oblasti, stane se členem pracovní oblasti, ke kterému byl přesunut. Pokud položka není v rámci všechny pracovní plochy, automaticky stane členem první pracovní oblasti (index 0). Pokud chcete vytvořit položku a mít ji umístit do konkrétní pracovní oblasti, budete muset vytvořit položku a poté ho přesuňte do požadované pracovní oblasti s volání [SetItemPosition](../mfc/reference/clistctrl-class.md#setitemposition). Druhý následující příklad ukazuje tento postup.  
  
 Následující příklad implementuje čtyři pracovní oblasti (`rcWorkAreas`), rovna velikosti s 10. pixelů celou ohraničení pro každý pracovní oblasti v ovládacím prvku seznam (`m_WorkAreaListCtrl`).  
  
 [!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]  
  
 Volání [ApproximateViewRect](../mfc/reference/clistctrl-class.md#approximateviewrect) došlo ke zjištění odhadu celkový oblasti vyžadována k zobrazení všech položek v jedné oblasti. Tento odhad je poté rozdělen do čtyř oblastí a vyplní s 5. pixelů celou ohraničení.  
  
 Další příklad přiřadí existující položky seznamu ke každé skupině (`rcWorkAreas`) a aktualizuje zobrazení ovládacího prvku (`m_WorkAreaListCtrl`) k dokončení účinek.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

