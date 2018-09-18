---
title: Použití zobrazení záznamů (přístup k datům MFC) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4107b5e19020843fa50495153841ebcba64301ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077682"
---
# <a name="using-a-record-view--mfc-data-access"></a>Použití zobrazení záznamů (přístup k datům MFC)

Toto téma vysvětluje, jak může často přizpůsobit výchozí kód pro zobrazení záznamů, které průvodce zapíše za vás. Obvykle je vhodné omezit výběr záznamu [filtr](../data/odbc/recordset-filtering-records-odbc.md) nebo [parametry](../data/odbc/recordset-parameterizing-a-recordset-odbc.md), možná [řazení](../data/odbc/recordset-sorting-records-odbc.md) záznamy, přizpůsobení příkazu SQL.  
  
Pomocí `CRecordView` je skoro stejné jako při použití [CFormView](../mfc/reference/cformview-class.md). Základní přístupem je použití zobrazení záznamů pro zobrazení a případně k aktualizaci záznamů z jedné sady záznamů. Kromě toho můžete chtít použít jiné sady záznamů také, jak je popsáno v [zobrazení záznamů: naplnění seznamu druhou sadou záznamů](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).  
  
## <a name="see-also"></a>Viz také  

[Zobrazení záznamů (přístup k datům MFC)](../data/record-views-mfc-data-access.md)<br/>
[Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)