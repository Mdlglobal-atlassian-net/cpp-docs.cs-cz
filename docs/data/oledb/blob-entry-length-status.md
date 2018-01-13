---
title: BLOB_ENTRY_LENGTH_STATUS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BLOB_ENTRY_LENGTH_STATUS
dev_langs: C++
helpviewer_keywords: BLOB_ENTRY_LENGTH_STATUS macro
ms.assetid: 09da67de-421b-4853-9a26-760e38324502
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1362fd9b74e415a2502c64245b580acec6fba729
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="blobentrylengthstatus"></a>BLOB_ENTRY_LENGTH_STATUS
Použít s `BEGIN_COLUMN_MAP` a `END_COLUMN_MAP` pro vazbu binární rozsáhlý objekt ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)). Podobně jako [BLOB_ENTRY](../../data/oledb/blob-entry.md)kromě toho, že tento makro také získá délku a stav sloupce objektů BLOB.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BLOB_ENTRY_LENGTH_STATUS(  
nOrdinal  
,   
IID  
,   
flags  
,   
data  
, length, status )  
```  
  
#### <a name="parameters"></a>Parametry  
 `nOrdinal`  
 [v] Číslo sloupce.  
  
 *IDENTIFIKÁTORY IID*  
 [v] Identifikátor GUID, například rozhraní **IDD_ISequentialStream**používané k načtení objektu BLOB.  
  
 `flags`  
 [v] Režim úložiště flags podle definice OLE strukturovaných modelu úložiště (například **STGM_READ**).  
  
 `data`  
 [v] Odpovídající datových členů v záznamu uživatele.  
  
 *Délka*  
 [out] (Skutečné) délka v bajtech sloupci objektů BLOB.  
  
 *Stav*  
 [out] Stav sloupce dat objektů BLOB.  
  
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
 [BLOB_ENTRY_LENGTH](../../data/oledb/blob-entry-length.md)   
 [BLOB_ENTRY_STATUS](../../data/oledb/blob-entry-status.md)