---
title: PROVIDER_COLUMN_ENTRY_TYPE_LENGTH | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
dev_langs: C++
helpviewer_keywords: PROVIDER_COLUMN_ENTRY_TYPE_LENGTH macro
ms.assetid: a60b1a8b-0903-4ff4-91ec-ed62126449fb
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8b7f072c2a83bb476c4e088d36643e21bd075473
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="providercolumnentrytypelength"></a>PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
Představuje konkrétní sloupec podporována zprostředkovatelem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(  
name  
, ordinal, dbtype, size, member )  
```  
  
#### <a name="parameters"></a>Parametry  
 *Jméno*  
  
 [v] Název sloupce.  
  
 `ordinal`  
 [v] Číslo sloupce. Pokud sloupec je sloupec záložky, číslo sloupce nesmí být 0.  
  
 `dbtype`  
 [v] Datový typ v [DBTYPE](https://msdn.microsoft.com/en-us/library/ms711251.aspx).  
  
 `size`  
 [v] Sloupec velikost v bajtech.  
  
 `member`  
 [v] Členské proměnné ve třídě data, která ukládá data.  
  
## <a name="remarks"></a>Poznámky  
 Podobně jako [PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md) , ale také vám umožní určit typ sloupce dat, jakož i velikost.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Makra pro šablony zprostředkovatele technologie OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)