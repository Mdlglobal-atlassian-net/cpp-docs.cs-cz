---
title: BLOB_ENTRY_LENGTH | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BLOB_ENTRY_LENGTH
dev_langs:
- C++
helpviewer_keywords:
- BLOB_ENTRY_LENGTH macro
ms.assetid: 832d21ab-5fdd-49ad-af6e-4fca5722ec93
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e8fe67acf9e0f6217e090ecb77fa63846f506543
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="blobentrylength"></a>BLOB_ENTRY_LENGTH
Použít s `BEGIN_COLUMN_MAP` a `END_COLUMN_MAP` pro vazbu binární rozsáhlý objekt ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)). Podobně jako [BLOB_ENTRY](../../data/oledb/blob-entry.md)kromě toho, že tento makro také získá délku v bajtech sloupce objektů BLOB.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `nOrdinal`  
 [v] Číslo sloupce.  
  
 *IID*  
 [v] Identifikátor GUID, například rozhraní **IDD_ISequentialStream**používané k načtení objektu BLOB.  
  
 `flags`  
 [v] Režim úložiště flags podle definice OLE strukturovaných modelu úložiště (například **STGM_READ**).  
  
 `data`  
 [v] Odpovídající datových členů v záznamu uživatele.  
  
 *Délka*  
 [out] \(Skutečné) délka v bajtech sloupci objektů BLOB.  
  
## <a name="example"></a>Příklad  
 V tématu [jak můžete načíst objekt BLOB?](../../data/oledb/retrieving-a-blob.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB_ENTRY](../../data/oledb/blob-entry.md)   
 [BLOB_ENTRY_LENGTH_STATUS](../../data/oledb/blob-entry-length-status.md)   
 [BLOB_ENTRY_STATUS](../../data/oledb/blob-entry-status.md)