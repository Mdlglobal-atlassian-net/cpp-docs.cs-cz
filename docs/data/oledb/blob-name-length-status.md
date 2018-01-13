---
title: BLOB_NAME_LENGTH_STATUS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BLOB_NAME_LENGTH_STATUS
dev_langs: C++
helpviewer_keywords: BLOB_NAME_LENGTH_STATUS macro
ms.assetid: 3cc3ec8d-80a5-4522-848a-123fcaee58cb
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b0f385d0727fa0f66c414aef7e9e612b21624c02
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="blobnamelengthstatus"></a>BLOB_NAME_LENGTH_STATUS
Použít s `BEGIN_COLUMN_MAP` a `END_COLUMN_MAP` pro vazbu binární rozsáhlý objekt ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)). Podobně jako [BLOB_NAME](../../data/oledb/blob-name.md)kromě toho, že tento makro také získá délku a stav sloupce dat objektů BLOB.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BLOB_NAME_LENGTH_STATUS(  
pszName  
,   
IID  
,   
flags  
,   
data  
,   
length  
, status )  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
 [v] Ukazatel na název sloupce. Název musí být řetězec znaků Unicode. Toho lze dosáhnout vložením "L" před název, například: `L"MyColumn"`.  
  
 *IDENTIFIKÁTORY IID*  
 [v] Identifikátor GUID, například rozhraní **IDD_ISequentialStream**používané k načtení objektu BLOB.  
  
 `flags`  
 [v] Režim úložiště flags podle definice OLE strukturovaných modelu úložiště (například **STGM_READ**).  
  
 `data`  
 [v] Odpovídající datových členů v záznamu uživatele.  
  
 *Délka*  
 [out] (Skutečné) délka v bajtech sloupci objektů BLOB.  
  
 *Stav*  
 [out] Stav pole objektů BLOB.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB_NAME](../../data/oledb/blob-name.md)   
 [BLOB_NAME_LENGTH](../../data/oledb/blob-name-length.md)   
 [BLOB_NAME_STATUS](../../data/oledb/blob-name-status.md)