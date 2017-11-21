---
title: CUsagePrivileges, CUsagePrivilegeInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- m_szObjectCatalog
- CUsagePrivilegeInfo
- m_bIsGrantable
- OBJECT_NAME
- m_szPrivilegeType
- OBJECT_SCHEMA
- IS_GRANTABLE
- CUsagePrivileges
- m_szGrantor
- GRANTOR
- GRANTEE
- m_szObjectSchema
- OBJECT_CATALOG
- m_szObjectType
- m_szObjectName
- m_szGrantee
- OBJECT_TYPE
dev_langs: C++
helpviewer_keywords:
- OBJECT_NAME
- GRANTOR
- OBJECT_CATALOG
- CUsagePrivileges typedef class
- m_szPrivilegeType
- OBJECT_SCHEMA
- m_szObjectSchema
- m_szObjectType
- IS_GRANTABLE
- OBJECT_TYPE
- CUsagePrivilegeInfo parameter class
- m_szGrantee
- m_szObjectCatalog
- m_szGrantor
- GRANTEE
- m_bIsGrantable
- m_szObjectName
ms.assetid: 09460e7f-3947-4837-ad1e-407b94acedb8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 874ca73ceae98d7603b7318b093645a0cd8104dc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cusageprivileges-cusageprivilegeinfo"></a>CUsagePrivileges, CUsagePrivilegeInfo
Call – třída definice typedef **CUsagePrivileges** k implementaci jeho – třída parametru **CUsagePrivilegeInfo**.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) pro další informace o použití definiční třídy typů.  
  
 Tato třída identifikuje využití oprávnění na objekty definované v katalogu, které jsou k dispozici nebo udělují daného uživatele.  
  
 Následující tabulka uvádí členy třídy dat a jejich odpovídající OLE DB sloupce. V tématu [USAGE_PRIVILEGES řádků](https://msdn.microsoft.com/en-us/library/ms722743.aspx) v *referenční příručka programátora technologie OLE DB* Další informace o schématu a sloupců.  
  
|Datové členy|Sloupce OLE DB|  
|------------------|--------------------|  
|m_szGrantor|GRANTOR|  
|m_szGrantee|GRANTEE|  
|m_szObjectCatalog|OBJECT_CATALOG|  
|m_szObjectSchema|OBJECT_SCHEMA|  
|m_szObjectName|OBJECT_NAME|  
|m_szObjectType|OBJECT_TYPE|  
|m_szPrivilegeType|PRIVILEGE_TYPE|  
|m_bIsGrantable|IS_GRANTABLE|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldbsch.h  
  
## <a name="see-also"></a>Viz také  
 [CRestrictions – třída](../../data/oledb/crestrictions-class.md)