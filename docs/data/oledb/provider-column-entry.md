---
title: PROVIDER_COLUMN_ENTRY | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROVIDER_COLUMN_ENTRY
dev_langs: C++
helpviewer_keywords: PROVIDER_COLUMN_ENTRY macro
ms.assetid: 7921cfc1-aa9c-493e-8fc4-9d4294cafe72
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2e8a97beb60dcc08fb442322191d8a515bdbdbc0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="providercolumnentry"></a>PROVIDER_COLUMN_ENTRY
Představuje konkrétní sloupec podporována zprostředkovatelem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PROVIDER_COLUMN_ENTRY (  
name  
, ordinal, member )  
```  
  
#### <a name="parameters"></a>Parametry  
 *Jméno*  
 [v] Název sloupce.  
  
 `ordinal`  
 [v] Číslo sloupce. Pokud sloupec je sloupec záložky, číslo sloupce nesmí být 0.  
  
 `member`  
 [v] Členské proměnné v `dataClass` odpovídající sloupce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Makra pro šablony zprostředkovatele technologie OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)