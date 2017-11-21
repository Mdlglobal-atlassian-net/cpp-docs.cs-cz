---
title: CViewColumnUsage, CViewColumnInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- m_szTableSchema
- m_szCatalog
- m_nColumnPropID
- COLUMN_GUID
- m_szColumnName
- m_szTableCatalog
- CViewColumnInfo
- m_szSchema
- CViewColumnUsage
- COLUMN_PROPID
- m_guidColumn
- m_szTableName
- m_szName
dev_langs: C++
helpviewer_keywords:
- COLUMN_PROPID
- m_szSchema
- m_szTableSchema
- TABLE_CATALOG
- m_szCatalog
- TABLE_NAME
- m_nColumnPropID
- CViewColumnInfo parameter class
- TABLE_SCHEMA
- m_szColumnName
- COLUMN_NAME
- m_szName
- m_szTableCatalog
- CViewColumnUsage typedef class
- m_szTableName
- COLUMN_GUID
- m_guidColumn
ms.assetid: 4af14d6b-b224-4d72-b035-9d3aaacde32f
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 834f1f0bd60bb573c5371a8a5aa3e2185bb115d2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cviewcolumnusage-cviewcolumninfo"></a>CViewColumnUsage, CViewColumnInfo
Call – třída definice typedef **CViewColumnUsage** k implementaci jeho – třída parametru **CViewColumnInfo**.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) pro další informace o použití definiční třídy typů.  
  
 Tato třída identifikuje sloupce v zobrazení tabulek, které jsou definované v katalogu a vlastníkem daného uživatele, jsou závislé.  
  
 Následující tabulka uvádí členy třídy dat a jejich odpovídající OLE DB sloupce. V tématu [VIEW_COLUMN_USAGE řádků](https://msdn.microsoft.com/en-us/library/ms714896.aspx) v *referenční příručka programátora technologie OLE DB* Další informace o schématu a sloupců.  
  
|Datové členy|Sloupce OLE DB|  
|------------------|--------------------|  
|m_szCatalog|VIEW_CATALOG|  
|m_szSchema|VIEW_SCHEMA|  
|m_szName|VIEW_NAME|  
|m_szTableCatalog|TABLE_CATALOG|  
|m_szTableSchema|TABLE_SCHEMA|  
|m_szTableName|TABLE_NAME|  
|m_szColumnName|COLUMN_NAME|  
|m_guidColumn|COLUMN_GUID|  
|m_nColumnPropID|COLUMN_PROPID|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldbsch.h  
  
## <a name="see-also"></a>Viz také  
 [CRestrictions – třída](../../data/oledb/crestrictions-class.md)