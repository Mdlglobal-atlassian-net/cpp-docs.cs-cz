---
title: "Použití zobrazení záznamů (MFC Data Access) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4d37f40169330fe878eee326628bd26bef9ca8d8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-a-record-view--mfc-data-access"></a>Použití zobrazení záznamů (Data MFC Access)
Toto téma vysvětluje, jak může často přizpůsobit výchozí kód pro zobrazení záznamů, které pro vás zapisuje průvodce. Obvykle je vhodné omezit výběr záznamu [filtru](../data/odbc/recordset-filtering-records-odbc.md) nebo [parametry](../data/odbc/recordset-parameterizing-a-recordset-odbc.md), případně [řazení](../data/odbc/recordset-sorting-records-odbc.md) záznamy, přizpůsobení příkazu SQL.  
  
 Pomocí `CRecordView` je podobný jako při použití [CFormView](../mfc/reference/cformview-class.md). Základní postup je použití zobrazení záznamů zobrazíte a případně k aktualizaci záznamů jedné sady záznamů. Kromě toho, můžete chtít použít jiné sady záznamů také, jak je popsáno v [zobrazení záznamů: naplnění seznamu z druhé sady záznamů](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení záznamů (Data MFC Access)](../data/record-views-mfc-data-access.md)   
 [Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)