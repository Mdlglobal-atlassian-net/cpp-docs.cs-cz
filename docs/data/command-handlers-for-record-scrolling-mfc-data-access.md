---
title: "Příkaz obslužné rutiny pro záznam posouvání (MFC Data Access) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d3164cfd8a7d78191f2076637b51d96bb45f2293
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>Obslužné rutiny příkazů pro záznam posouvání (Data MFC Access)
[CRecordView](../mfc/reference/crecordview-class.md) třída poskytuje výchozí příkaz pro následující standardní příkazy zpracování:  
  
-   **ID_RECORD_MOVE_FIRST**  
  
-   **ID_RECORD_MOVE_LAST**  
  
-   **ID_RECORD_MOVE_NEXT**  
  
-   **ID_RECORD_MOVE_PREV**  
  
 `OnMove` – Členská funkce poskytuje výchozí příkaz zpracování pro všechny čtyři příkazy, které se pohybují mezi záznamy. Tyto příkazy jsou používány, RFX (nebo DFX) načte nový záznam do sady záznamů v polích a DDX přesune hodnoty do ovládacích prvků záznamů formuláře. Informace o RFX najdete v tématu [výměna pole záznamu (RFX)](../data/odbc/record-field-exchange-rfx.md).  
  
> [!NOTE]
>  Nezapomeňte použít tyto identifikátory standardních příkazů pro všechny objekty uživatelského rozhraní přidružené příkazy standardní záznamu navigace.  
  
## <a name="see-also"></a>Viz také  
 [Podpora navigace v zobrazení záznamů](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)