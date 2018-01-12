---
title: CReferentialConstraints, CReferentialConstraintInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- m_szUniqueName
- m_szCatalog
- DELETE_RULE
- m_szUniqueCatalog
- CONSTRAINT_NAME
- CReferentialConstraintInfo
- MATCH_OPTION
- m_szSchema
- m_szDeleteRule
- m_szUpdateRule
- m_szUniqueSchema
- CReferentialConstraints
- m_szName
- CONSTRAINT_CATALOG
- m_szMatchOption
- CONSTRAINT_SCHEMA
dev_langs: C++
helpviewer_keywords:
- m_szUniqueSchema
- DESCRIPTION class data member
- m_szSchema
- CONSTRAINT_CATALOG
- CReferentialConstraints typedef class
- m_szUniqueName
- m_szCatalog
- CONSTRAINT_NAME
- m_szDeleteRule
- DELETE_RULE
- MATCH_OPTION
- CONSTRAINT_SCHEMA
- m_szName
- m_szDescription
- m_szMatchOption
- m_szUniqueCatalog
- m_szUpdateRule
- CReferentialConstraintInfo parameter class
ms.assetid: 5d485358-be29-41c2-b0ce-19e023598e73
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 525d75ad244cac267b0f8b51dccf18210b504f2e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="creferentialconstraints-creferentialconstraintinfo"></a>CReferentialConstraints, CReferentialConstraintInfo
Call – třída definice typedef **CReferentialConstraints** k implementaci jeho – třída parametru **CReferentialConstraintInfo**.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) pro další informace o použití definiční třídy typů.  
  
 Tato třída identifikuje referenční omezení, definované v katalogu, které jsou vlastněny daného uživatele.  
  
 Následující tabulka uvádí členy třídy dat a jejich odpovídající OLE DB sloupce. V tématu [REFERENTIAL_CONSTRAINTS řádků](https://msdn.microsoft.com/en-us/library/ms719737.aspx) v *referenční příručka programátora technologie OLE DB* Další informace o schématu a sloupců.  
  
|Datové členy|Sloupce OLE DB|  
|------------------|--------------------|  
|m_szCatalog|CONSTRAINT_CATALOG|  
|m_szSchema|CONSTRAINT_SCHEMA|  
|m_szName|CONSTRAINT_NAME|  
|m_szUniqueCatalog|UNIQUE_CONSTRAINT_CATALOG|  
|m_szUniqueSchema|UNIQUE_CONSTRAINT_SCHEMA|  
|m_szUniqueName|UNIQUE_CONSTRAINT_NAME|  
|m_szMatchOption|MATCH_OPTION|  
|m_szUpdateRule|UPDATE_RULE|  
|m_szDeleteRule|DELETE_RULE|  
|m_szDescription|POPIS|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldbsch.h  
  
## <a name="see-also"></a>Viz také  
 [CRestrictions – třída](../../data/oledb/crestrictions-class.md)