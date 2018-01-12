---
title: CTablePrivileges, CTablePrivilegeInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- m_szCatalog
- m_bIsGrantable
- IS_GRANTABLE
- m_szType
- m_szSchema
- m_szGrantor
- GRANTOR
- GRANTEE
- CTablePrivileges
- CTablePrivilegeInfo
- m_szName
- m_szGrantee
dev_langs: C++
helpviewer_keywords:
- GRANTOR
- CTablePrivilegeInfo parameter class
- m_szSchema
- TABLE_CATALOG
- m_szType
- m_szCatalog
- TABLE_NAME
- IS_GRANTABLE
- TABLE_SCHEMA
- m_szName
- m_szGrantee
- CTablePrivileges typedef class
- m_szGrantor
- GRANTEE
- m_bIsGrantable
ms.assetid: ffcd6f73-022e-452a-8342-f2b9362d256b
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4af4debc152e2c1c84dcfd1fbd7f4950922fa7df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ctableprivileges-ctableprivilegeinfo"></a>CTablePrivileges, CTablePrivilegeInfo
Call – třída definice typedef **CTablePrivileges** k implementaci jeho – třída parametru **CTablePrivilegeInfo**.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) pro další informace o použití definiční třídy typů.  
  
 Tato třída identifikuje tabulky definované v katalogu, které jsou dostupné pro daného uživatele.  
  
 Následující tabulka uvádí členy třídy dat a jejich odpovídající OLE DB sloupce. V tématu [TABLE_PRIVILEGES řádků](https://msdn.microsoft.com/en-us/library/ms725428.aspx) v *referenční příručka programátora technologie OLE DB* Další informace o schématu a sloupců.  
  
|Datové členy|Sloupce OLE DB|  
|------------------|--------------------|  
|m_szGrantor|GRANTOR|  
|m_szGrantee|GRANTEE|  
|m_szCatalog|TABLE_CATALOG|  
|m_szSchema|TABLE_SCHEMA|  
|m_szName|TABLE_NAME|  
|m_szType|PRIVILEGE_TYPE|  
|m_bIsGrantable|IS_GRANTABLE|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldbsch.h  
  
## <a name="see-also"></a>Viz také  
 [CRestrictions – třída](../../data/oledb/crestrictions-class.md)