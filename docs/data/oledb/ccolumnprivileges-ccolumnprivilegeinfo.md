---
title: CColumnPrivileges, CColumnPrivilegeInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- m_szTableSchema
- CColumnPrivileges
- m_bIsGrantable
- m_nColumnPropID
- m_szPrivilegeType
- COLUMN_GUID
- IS_GRANTABLE
- m_szColumnName
- m_szTableCatalog
- m_szGrantor
- GRANTOR
- GRANTEE
- COLUMN_PROPID
- m_guidColumn
- COLUMN_PRIVILEGES
- m_szTableName
- CColumnPrivilegeInfo
- m_szGrantee
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_PROPID
- GRANTOR
- m_szPrivilegeType
- m_szTableSchema
- TABLE_CATALOG
- TABLE_NAME
- COLUMN_PRIVILEGES
- IS_GRANTABLE
- m_nColumnPropID
- TABLE_SCHEMA
- m_szColumnName
- COLUMN_NAME
- m_szTableCatalog
- m_szGrantee
- m_szGrantor
- m_szTableName
- CColumnPrivileges typedef class
- COLUMN_GUID
- GRANTEE
- m_guidColumn
- CColumnPrivilegeInfo parameter class
- m_bIsGrantable
ms.assetid: 245df365-421f-43c6-9fcd-fb2197c871c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 57ccdea5fbafea147da6c866dc0cc67c2f30b0ac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095700"
---
# <a name="ccolumnprivileges-ccolumnprivilegeinfo"></a>CColumnPrivileges, CColumnPrivilegeInfo
Call – třída definice typedef **CColumnPrivileges** k implementaci jeho – třída parametru **CColumnPrivilegeInfo**.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) pro další informace o použití definiční třídy typů.  
  
 Tato třída identifikuje oprávnění na sloupce tabulky definované v katalogu, které jsou k dispozici nebo udělené pomocí daného uživatele.  
  
 Následující tabulka uvádí členy třídy dat a jejich odpovídající OLE DB sloupce. V tématu [COLUMN_PRIVILEGES řádků](https://msdn.microsoft.com/en-us/library/ms715800.aspx) v *referenční příručka programátora technologie OLE DB* Další informace o schématu a sloupců.  
  
|Datové členy|Sloupce OLE DB|  
|------------------|--------------------|  
|m_szGrantor|GRANTOR|  
|m_szGrantee|GRANTEE|  
|m_szTableCatalog|TABLE_CATALOG|  
|m_szTableSchema|TABLE_SCHEMA|  
|m_szTableName|TABLE_NAME|  
|m_szColumnName|COLUMN_NAME|  
|m_guidColumn|COLUMN_GUID|  
|m_nColumnPropID|COLUMN_PROPID|  
|m_szPrivilegeType|PRIVILEGE_TYPE|  
|m_bIsGrantable|IS_GRANTABLE|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldbsch.h  
  
## <a name="see-also"></a>Viz také  
 [CRestrictions – třída](../../data/oledb/crestrictions-class.md)