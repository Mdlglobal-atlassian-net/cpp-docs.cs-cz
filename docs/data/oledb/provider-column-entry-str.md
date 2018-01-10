---
title: PROVIDER_COLUMN_ENTRY_STR | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROVIDER_COLUMN_ENTRY_STR
dev_langs: C++
helpviewer_keywords: PROVIDER_COLUMN_ENTRY_STR macro
ms.assetid: f1c27dd6-9ab8-4821-8685-d4dd15e76e88
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fc45826fed148b2d3d7990ce512bc9a1861fdff0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="providercolumnentrystr"></a>PROVIDER_COLUMN_ENTRY_STR
Představuje konkrétní sloupec podporována zprostředkovatelem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PROVIDER_COLUMN_ENTRY_STR(  
name  
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
 Použití tohoto makra, když se považuje za data ve sloupci [typem DBTYPE_STR](https://msdn.microsoft.com/en-us/library/ms711251.aspx).  
  
## <a name="example"></a>Příklad  
 V tématu [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Makra pro šablony zprostředkovatele technologie OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)