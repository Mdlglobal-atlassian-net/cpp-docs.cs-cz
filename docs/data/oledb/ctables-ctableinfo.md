---
title: CTables, CTableInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- m_szCatalog
- TABLE_SCHEMA
- CTables
- TABLE_NAME
- TABLE_CATALOG
- CTableInfo
- m_guidTable
- m_szType
- m_szSchema
- m_szName
- TABLE_GUID
dev_langs: C++
helpviewer_keywords:
- DESCRIPTION class data member
- m_szSchema
- TABLE_CATALOG
- m_szType
- m_szCatalog
- TABLE_NAME
- TABLE_SCHEMA
- TABLE_GUID
- m_szName
- m_szDescription
- CTables typedef class
- m_guidTable
- CTableInfo parameter class
ms.assetid: 57670f1b-ba99-43b0-b406-4c75b44f14f6
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6bb693d549420d0fac28e2952ea96789d8d23989
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ctables-ctableinfo"></a>CTables, CTableInfo
Call – třída definice typedef **CTables** k implementaci jeho – třída parametru **CTableInfo**.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) pro další informace o použití definiční třídy typů.  
  
 Tato třída identifikuje oprávnění na tabulky definované v katalogu, které jsou k dispozici nebo udělují daného uživatele.  
  
 Následující tabulka uvádí členy třídy dat a jejich odpovídající OLE DB sloupce. V tématu [řádků tabulky](https://msdn.microsoft.com/en-us/library/ms716980.aspx) v *referenční příručka programátora technologie OLE DB* Další informace o schématu a sloupců.  
  
|Datové členy|Sloupce OLE DB|  
|------------------|--------------------|  
|m_szCatalog|TABLE_CATALOG|  
|m_szSchema|TABLE_SCHEMA|  
|m_szName|TABLE_NAME|  
|m_szType|TABLE_TYPE|  
|m_guidTable|TABLE_GUID|  
|m_szDescription|POPIS|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldbsch.h  
  
## <a name="see-also"></a>Viz také  
 [CRestrictions – třída](../../data/oledb/crestrictions-class.md)