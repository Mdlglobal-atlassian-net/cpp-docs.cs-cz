---
title: PROVIDER_COLUMN_ENTRY_FIXED | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROVIDER_COLUMN_ENTRY_FIXED
dev_langs: C++
helpviewer_keywords: PROVIDER_COLUMN_ENTRY_FIXED macro
ms.assetid: 71f9c9aa-56a0-488b-96ba-5c72da9c71d0
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e404e18a072650d89f3987d8e8f0e286240d022a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="providercolumnentryfixed"></a>PROVIDER_COLUMN_ENTRY_FIXED
Představuje konkrétní sloupec podporována zprostředkovatelem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PROVIDER_COLUMN_ENTRY_FIXED(  
name  
, ordinal, dbtype, member )  
```  
  
#### <a name="parameters"></a>Parametry  
 *Jméno*  
 [v] Název sloupce.  
  
 `ordinal`  
 [v] Číslo sloupce. Pokud sloupec je sloupec záložky, číslo sloupce nesmí být 0.  
  
 `dbtype`  
 [v] Datový typ v [DBTYPE](https://msdn.microsoft.com/en-us/library/ms711251.aspx).  
  
 `member`  
 [v] Členské proměnné v `dataClass` která ukládá data.  
  
## <a name="remarks"></a>Poznámky  
 Umožňuje zadat datový typ sloupce.  
  
## <a name="example"></a>Příklad  
 V tématu [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Makra pro šablony zprostředkovatele technologie OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)