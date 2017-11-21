---
title: BLOB_ENTRY_STATUS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BLOB_ENTRY_STATUS
dev_langs: C++
helpviewer_keywords: BLOB_ENTRY_STATUS macro
ms.assetid: 191007f4-dfcc-4ae2-a7fc-6f7899accc9f
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0cc0805147908703b880cb826b0363acecfa4902
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="blobentrystatus"></a>BLOB_ENTRY_STATUS
Použít s `BEGIN_COLUMN_MAP` nebo `BEGIN_ACCESSOR_MAP` pro vazbu binární rozsáhlý objekt ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)). Podobně jako [BLOB_ENTRY](../../data/oledb/blob-entry.md)kromě toho, že tento makro také získá stav sloupci objektů BLOB.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BLOB_ENTRY_STATUS(  
nOrdinal  
,   
IID  
,   
flags  
,   
data  
,   
status  
 )  
  
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
  
 *Stav*  
 [out] Stav pole objektů BLOB.  
  
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
 [BLOB_ENTRY_LENGTH_STATUS](../../data/oledb/blob-entry-length-status.md)