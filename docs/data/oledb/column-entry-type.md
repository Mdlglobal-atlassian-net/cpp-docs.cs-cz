---
title: COLUMN_ENTRY_TYPE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- COLUMN_ENTRY_TYPE
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_ENTRY_TYPE macro
ms.assetid: ac424261-ff6c-443b-a197-2cec8d78d738
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2a653e863e8965efda55837124e93454820449de
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="columnentrytype"></a>COLUMN_ENTRY_TYPE
Představuje vazbu ke konkrétní sloupec v databázi. Podporuje `type` parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `nOrdinal`  
 [v] Číslo sloupce.  
  
 `wType`  
 [v] Datový typ sloupce položky.  
  
 `data`  
 [v] Odpovídající datových členů v záznamu uživatele.  
  
## <a name="remarks"></a>Poznámky  
 Toto makro je specializovaná varianta [COLUMN_ENTRY](../../data/oledb/column-entry.md) – makro poskytující prostředek sloužící k určení datového typu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)