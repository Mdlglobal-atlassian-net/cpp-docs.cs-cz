---
title: CForeignKeys, CForeignKeysInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- m_nOrdinal
- m_szPKColumnName
- FK_TABLE_NAME
- m_guidFKColumn
- FK_COLUMN_NAME
- m_guidPKColumn
- DELETE_RULE
- m_szPKTableSchema
- FK_COLUMN_PROPID
- m_nFKColumnPropID
- m_szFKTableCatalog
- CForeignKeysInfo
- FK_TABLE_SCHEMA
- m_szPKTableCatalog
- m_szDeleteRule
- m_szUpdateRule
- m_szPKTableName
- m_szFKTableSchema
- ORDINAL
- m_nPKColumnPropID
- m_szFKColumnName
- FK_TABLE_CATALOG
- FK_COLUMN_GUID
- m_szFKTableName
- CForeignKeys
dev_langs:
- C++
helpviewer_keywords:
- m_szPKTableCatalog
- FK_COLUMN_GUID
- m_szPKColumnName
- m_szFKTableName
- ORDINAL data member
- m_nPKColumnPropID
- m_szDeleteRule
- DELETE_RULE
- m_guidFKColumn
- FK_COLUMN_PROPID
- m_szPKTableSchema
- m_szFKTableCatalog
- CForeignKeysInfo parameter class
- m_szFKTableSchema
- FK_TABLE_SCHEMA
- FK_COLUMN_NAME
- m_szUpdateRule
- m_szFKColumnName
- FK_TABLE_CATALOG
- m_nOrdinal
- m_szPKTableName
- CForeignKeys typedef class
- m_nFKColumnPropID
- m_guidPKColumn
- FK_TABLE_NAME
ms.assetid: 1c401a4a-0827-4255-9214-bc893e1cd79d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e31251156e84a6befec036f9e27c45f3aba1d895
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="cforeignkeys-cforeignkeysinfo"></a>CForeignKeys, CForeignKeysInfo
Call – třída definice typedef **CForeignKeys** k implementaci jeho – třída parametru **CForeignKeysInfo**.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) pro další informace o použití definiční třídy typů.  
  
 Tato třída identifikuje sloupce cizích klíčů v katalogu definované daného uživatele.  
  
 Následující tabulka uvádí členy třídy dat a jejich odpovídající OLE DB sloupce. V tématu [FOREIGN_KEYS řádků](https://msdn.microsoft.com/en-us/library/ms711276.aspx) v *referenční příručka programátora technologie OLE DB* Další informace o schématu a sloupců.  
  
|Datové členy|Sloupce OLE DB|  
|------------------|--------------------|  
|m_szPKTableCatalog|PK_TABLE_CATALOG|  
|m_szPKTableSchema|PK_TABLE_SCHEMA|  
|m_szPKTableName|PK_TABLE_NAME|  
|m_szPKColumnName|PK_COLUMN_NAME|  
|m_guidPKColumn|PK_COLUMN_GUID|  
|m_nPKColumnPropID|PK_COLUMN_PROPID|  
|m_szFKTableCatalog|FK_TABLE_CATALOG|  
|m_szFKTableSchema|FK_TABLE_SCHEMA|  
|m_szFKTableName|FK_TABLE_NAME|  
|m_szFKColumnName|FK_COLUMN_NAME|  
|m_guidFKColumn|FK_COLUMN_GUID|  
|m_nFKColumnPropID|FK_COLUMN_PROPID|  
|m_nOrdinal|POŘADÍ|  
|m_szUpdateRule|UPDATE_RULE|  
|m_szDeleteRule|DELETE_RULE|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldbsch.h  
  
## <a name="see-also"></a>Viz také  
 [CRestrictions – třída](../../data/oledb/crestrictions-class.md)