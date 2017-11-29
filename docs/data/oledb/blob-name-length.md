---
title: BLOB_NAME_LENGTH | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BLOB_NAME_LENGTH
dev_langs: C++
helpviewer_keywords: BLOB_NAME_LENGTH macro
ms.assetid: 38150260-a127-486d-a7ab-0d01b731b6fd
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f0367d92ecb592f0d974b8083362e2287eda97da
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="blobnamelength"></a>BLOB_NAME_LENGTH
Použít s `BEGIN_COLUMN_MAP` a `END_COLUMN_MAP` pro vazbu binární rozsáhlý objekt ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)). Podobně jako [BLOB_NAME](../../data/oledb/blob-name.md)kromě toho, že tento makro také získá délku v bajtech sloupce dat objektů BLOB.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BLOB_NAME_LENGTH(  
pszName  
,   
IID  
,   
flags  
,   
data  
,   
length )  
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
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB_NAME](../../data/oledb/blob-name.md)   
 [BLOB_NAME_LENGTH_STATUS](../../data/oledb/blob-name-length-status.md)   
 [BLOB_NAME_STATUS](../../data/oledb/blob-name-status.md)