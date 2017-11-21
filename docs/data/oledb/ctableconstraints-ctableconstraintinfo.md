---
title: CTableConstraints, CTableConstraintInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- m_szTableSchema
- CONSTRAINT_TYPE
- m_szCatalog
- CTableConstraints
- m_bInitiallyDeferred
- CONSTRAINT_NAME
- m_szTableCatalog
- m_szType
- m_szSchema
- INITIALLY_DEFERRED
- CTableConstraintInfo
- m_szTableName
- m_bIsDeferrable
- m_szName
- CONSTRAINT_CATALOG
- CONSTRAINT_SCHEMA
- IS_DEFERRABLE
dev_langs: C++
helpviewer_keywords:
- DESCRIPTION class data member
- CTableConstraints typedef class
- IS_DEFERRABLE
- m_szSchema
- m_bInitiallyDeferred
- CONSTRAINT_CATALOG
- m_szTableSchema
- TABLE_CATALOG
- m_szType
- m_szCatalog
- TABLE_NAME
- CONSTRAINT_NAME
- CONSTRAINT_TYPE
- CONSTRAINT_SCHEMA
- TABLE_SCHEMA
- m_szName
- m_szTableCatalog
- m_szDescription
- CTableConstraintInfo parameter class
- m_szTableName
- INITIALLY_DEFERRED
- m_bIsDeferrable
ms.assetid: aaa07ade-0bfa-41d0-94df-8342152a4ff0
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cda2e1ccfa479eb2b71a4a21f49b67b127e9984c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ctableconstraints-ctableconstraintinfo"></a>CTableConstraints, CTableConstraintInfo
Call – třída definice typedef **CTableConstraints** k implementaci jeho – třída parametru **CTableConstraintInfo**.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) pro další informace o použití definiční třídy typů.  
  
 Tato třída identifikuje tabulky omezení, definované v katalogu, které jsou vlastněny daného uživatele.  
  
 Následující tabulka uvádí členy třídy dat a jejich odpovídající OLE DB sloupce. V tématu [TABLE_CONSTRAINTS řádků](https://msdn.microsoft.com/en-us/library/ms715921.aspx) v *referenční příručka programátora technologie OLE DB* Další informace o schématu a sloupců.  
  
|Datové členy|Sloupce OLE DB|  
|------------------|--------------------|  
|m_szCatalog|CONSTRAINT_CATALOG|  
|m_szSchema|CONSTRAINT_SCHEMA|  
|m_szName|CONSTRAINT_NAME|  
|m_szTableCatalog|TABLE_CATALOG|  
|m_szTableSchema|TABLE_SCHEMA|  
|m_szTableName|TABLE_NAME|  
|m_szType|CONSTRAINT_TYPE|  
|m_bIsDeferrable|IS_DEFERRABLE|  
|m_bInitiallyDeferred|INITIALLY_DEFERRED|  
|m_szDescription|POPIS|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldbsch.h  
  
## <a name="see-also"></a>Viz také  
 [CRestrictions – třída](../../data/oledb/crestrictions-class.md)