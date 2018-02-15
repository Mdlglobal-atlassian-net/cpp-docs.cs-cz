---
title: BEGIN_SCHEMA_MAP | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BEGIN_SCHEMA_MAP
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_SCHEMA_MAP macro
ms.assetid: 4e751023-35bc-4efd-9018-5448dd1ad751
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b4ad46968919dec9500a826a4bbc5addfdea326a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="beginschemamap"></a>BEGIN_SCHEMA_MAP
Označuje začátek mapu schématu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      BEGIN_SCHEMA_MAP(SchemaClass);  
```  
  
#### <a name="parameters"></a>Parametry  
 *SchemaClass*  
 Třída, která obsahuje MAPY. Obvykle bude třída relace.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) ve Windows SDK pro další informace o schématu sady řádků.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Makra pro šablony zprostředkovatele technologie OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md)   
 [END_SCHEMA_MAP](../../data/oledb/end-schema-map.md)   
 [IDBSchemaRowsetImpl – třída](../../data/oledb/idbschemarowsetimpl-class.md)