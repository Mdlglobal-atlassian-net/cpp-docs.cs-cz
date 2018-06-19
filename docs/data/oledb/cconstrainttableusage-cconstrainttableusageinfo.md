---
title: CConstraintTableUsage, CConstraintTableUsageInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CConstraintTableUsageInfo
- CONSTRAINT_TABLE_USAGE
- m_szTableSchema
- m_szConstraintCatalog
- CONSTRAINT_NAME
- m_szTableCatalog
- m_szConstraintSchema
- m_szTableName
- CONSTRAINT_CATALOG
- CONSTRAINT_SCHEMA
- CConstraintTableUsage
- m_szConstraintName
dev_langs:
- C++
helpviewer_keywords:
- CConstraintTableUsage typedef class
- m_szConstraintCatalog
- CONSTRAINT_CATALOG
- m_szTableSchema
- CConstraintTableUsageInfo parameter class
- TABLE_CATALOG
- CONSTRAINT_TABLE_USAGE
- TABLE_NAME
- CONSTRAINT_NAME
- CONSTRAINT_SCHEMA
- TABLE_SCHEMA
- m_szTableCatalog
- m_szConstraintName
- m_szTableName
- m_szConstraintSchema
ms.assetid: 666b44de-3922-4c5e-ad17-d5ea27120174
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7662cc111101d63729b5cb37512988edd61ead14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095151"
---
# <a name="cconstrainttableusage-cconstrainttableusageinfo"></a>CConstraintTableUsage, CConstraintTableUsageInfo
Call – třída definice typedef **CConstraintTableUsage** k implementaci jeho – třída parametru **CConstraintTableUsageInfo**.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) pro další informace o použití definiční třídy typů.  
  
 Tato třída identifikuje tabulky používané referenční omezení, jedinečné omezení, omezení check a kontrolní výrazy, definované v katalogu a jejím vlastníkem daného uživatele.  
  
 Následující tabulka uvádí členy třídy dat a jejich odpovídající OLE DB sloupce. V tématu [CONSTRAINT_TABLE_USAGE řádků](https://msdn.microsoft.com/en-us/library/ms724522.aspx) v *referenční příručka programátora technologie OLE DB* Další informace o schématu a sloupců.  
  
|Datové členy|Sloupce OLE DB|  
|------------------|--------------------|  
|m_szTableCatalog|TABLE_CATALOG|  
|m_szTableSchema|TABLE_SCHEMA|  
|m_szTableName|TABLE_NAME|  
|m_szConstraintCatalog|CONSTRAINT_CATALOG|  
|m_szConstraintSchema|CONSTRAINT_SCHEMA|  
|m_szConstraintName|CONSTRAINT_NAME|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldbsch.h  
  
## <a name="see-also"></a>Viz také  
 [CRestrictions – třída](../../data/oledb/crestrictions-class.md)