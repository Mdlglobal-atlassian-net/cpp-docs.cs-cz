---
title: COLUMN_ENTRY | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- COLUMN_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_ENTRY macro
ms.assetid: a10aef29-6d70-49ec-b572-5b5c4abe1b46
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dc558a8238601a882f2b9e97a17e3ea56f14ea9c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="columnentry"></a>COLUMN_ENTRY
Představuje vazbu na sadě řádků konkrétní sloupec v dané sadě řádků.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_ENTRY(nOrdinal, data)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
 `nOrdinal`  
 [v] Číslo sloupce.  
  
 `data`  
 [v] Odpovídající datových členů v záznamu uživatele.  
  
## <a name="remarks"></a>Poznámky  
 `COLUMN_ENTRY` Makro se používá na těchto místech:  
  
-   Mezi [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.  
  
-   Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.  
  
-   Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklady v tématech makro [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)   
 [COLUMN_ENTRY_PS](../../data/oledb/column-entry-ps.md)   
 [COLUMN_ENTRY_PS_LENGTH](../../data/oledb/column-entry-ps-length.md)   
 [COLUMN_ENTRY_LENGTH](../../data/oledb/column-entry-length.md)   
 [COLUMN_ENTRY_LENGTH_STATUS](../../data/oledb/column-entry-length-status.md)   
 [COLUMN_ENTRY_PS_LENGTH_STATUS](../../data/oledb/column-entry-ps-length-status.md)   
 [COLUMN_ENTRY_STATUS](../../data/oledb/column-entry-status.md)   
 [COLUMN_ENTRY_PS_STATUS](../../data/oledb/column-entry-ps-status.md)   
 [COLUMN_ENTRY_TYPE](../../data/oledb/column-entry-type.md)   
 [COLUMN_ENTRY_TYPE_SIZE](../../data/oledb/column-entry-type-size.md)   
 [END_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)