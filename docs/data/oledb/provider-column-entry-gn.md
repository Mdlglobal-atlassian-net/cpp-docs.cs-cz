---
title: PROVIDER_COLUMN_ENTRY_GN | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- PROVIDER_COLUMN_ENTRY_GN
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_GN macro
ms.assetid: be77ba85-634c-4e28-832f-d2fa40413254
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ff73cda1e676387b4f8ca79ce1ef7cbf8fce13e1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="providercolumnentrygn"></a>PROVIDER_COLUMN_ENTRY_GN
Představuje konkrétní sloupec podporována zprostředkovatelem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
PROVIDER_COLUMN_ENTRY_GN (name  
, ordinal, flags, colSize, dbtype, precision, scale, guid )  
```  
  
#### <a name="parameters"></a>Parametry  
 *name*  
 [v] Název sloupce.  
  
 `ordinal`  
 [v] Číslo sloupce. Pokud sloupec je sloupec záložky, číslo sloupce nesmí být 0.  
  
 `flags`  
 [v] Určuje, jak je vrácená data. Najdete v článku `dwFlags` popis v [DBBINDING struktury](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 *colSize*  
 [v] Velikost sloupce.  
  
 `dbtype`  
 [v] Určuje datový typ hodnoty. Najdete v článku **wType** popis v [DBBINDING struktury](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 *přesnost*  
 [v] Určuje přesnost pro použití při získávání dat, pokud *dbType* je `DBTYPE_NUMERIC` nebo **DBTYPE_DECIMAL**. Najdete v článku **bPrecision** popis v [DBBINDING struktury](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 `scale`  
 [v] Označuje škálování pro použití při získávání dat, pokud je hodnota dbType `DBTYPE_NUMERIC` nebo **DBTYPE_DECIMAL**. Najdete v článku **bScale** popis v [DBBINDING struktury](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 `guid`  
 Sadu řádků schématu identifikátor GUID. V tématu [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) v *referenční příručka programátora technologie OLE DB* seznam sad řádků schématu a jejich identifikátory GUID.  
  
## <a name="remarks"></a>Poznámky  
 Umožňuje zadat velikost sloupce, datový typ, přesnost, měřítko a identifikátor GUID sady řádků schématu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Makra pro šablony zprostředkovatele technologie OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)