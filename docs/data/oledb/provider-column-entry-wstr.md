---
title: PROVIDER_COLUMN_ENTRY_WSTR | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- PROVIDER_COLUMN_ENTRY_WSTR
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_WSTR macro
ms.assetid: 70630bd5-d782-473b-9777-aebbbf5321c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: faa6630d8821065d056e922dbf4790265d2497f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104071"
---
# <a name="providercolumnentrywstr"></a>PROVIDER_COLUMN_ENTRY_WSTR
Představuje konkrétní sloupec podporována zprostředkovatelem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name  
, ordinal, member )  
```  
  
#### <a name="parameters"></a>Parametry  
 *Jméno*  
 [v] Název sloupce.  
  
 `ordinal`  
 [v] Číslo sloupce. Pokud sloupec je sloupec záložky, číslo sloupce nesmí být 0.  
  
 `member`  
 [v] Členské proměnné ve třídě data, která ukládá data.  
  
## <a name="remarks"></a>Poznámky  
 Použití tohoto makra, když jsou data sloupec s hodnotou null byl ukončen řetězec znaků Unicode, [DBTYPE_WSTR](https://msdn.microsoft.com/en-us/library/ms711251.aspx).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Makra pro šablony zprostředkovatele technologie OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)