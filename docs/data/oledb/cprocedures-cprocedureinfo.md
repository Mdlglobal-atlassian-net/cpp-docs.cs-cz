---
title: CProcedures, CProcedureInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CProcedures
- m_szCatalog
- CProcedureInfo
- m_szSchema
- m_szDefinition
- m_szName
- m_nType
dev_langs:
- C++
helpviewer_keywords:
- DESCRIPTION class data member
- m_szSchema
- m_nType
- m_szCatalog
- CProcedureInfo parameter class
- m_szName
- m_szDescription
- m_szDefinition
- CProcedures typedef class
ms.assetid: d0c7375e-ee0c-441d-aae6-6108150860a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 643904ac0a1887f2812ec19420180560dcd568b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096129"
---
# <a name="cprocedures-cprocedureinfo"></a>CProcedures, CProcedureInfo
Call – třída definice typedef **CProcedures** k implementaci jeho – třída parametru **CProcedureInfo**.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) pro další informace o použití definiční třídy typů.  
  
 Tato třída identifikuje postupy definované v katalogu, které jsou vlastněny daného uživatele.  
  
 Následující tabulka uvádí členy třídy dat a jejich odpovídající OLE DB sloupce. V tématu [postupy řádků](https://msdn.microsoft.com/en-us/library/ms724021.aspx) v *referenční příručka programátora technologie OLE DB* Další informace o schématu a sloupců.  
  
|Datové členy|Sloupce OLE DB|  
|------------------|--------------------|  
|m_szCatalog|PROCEDURE_CATALOG|  
|m_szSchema|PROCEDURE_SCHEMA|  
|m_szName|PROCEDURE_NAME|  
|m_nType|PROCEDURE_TYPE|  
|m_szDefinition|PROCEDURE_DEFINITION|  
|m_szDescription|POPIS|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldbsch.h  
  
## <a name="see-also"></a>Viz také  
 [CRestrictions – třída](../../data/oledb/crestrictions-class.md)