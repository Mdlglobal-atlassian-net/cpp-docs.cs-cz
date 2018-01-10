---
title: "CEnumeratorAccessor – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CEnumeratorAccessor
- CEnumeratorAccessor
- ATL.CEnumeratorAccessor
dev_langs: C++
helpviewer_keywords: CEnumeratorAccessor class
ms.assetid: 21e8e7ea-3511-4afe-b33f-d520f4ff82bb
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4a82b09a65cb4ebe6f0f796ba9aeb46ac5a2106a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cenumeratoraccessor-class"></a>CEnumeratorAccessor – třída
Používá [CEnumerator](../../data/oledb/cenumerator-class.md) pro přístup k datům z enumerátor sady řádků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CEnumeratorAccessor  
```  
  
## <a name="members"></a>Členové  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_bIsParent](../../data/oledb/cenumeratoraccessor-m-bisparent.md)|Proměnná určující, zda je enumerátor nadřazené enumerátor, pokud je řádek enumerátor.|  
|[m_nType](../../data/oledb/cenumeratoraccessor-m-ntype.md)|Proměnná, která určuje, zda řádek popisuje zdroj dat nebo enumerátor.|  
|[m_szDescription](../../data/oledb/cenumeratoraccessor-m-szdescription.md)|Popis zdroje dat nebo enumerátor.|  
|[m_szName](../../data/oledb/cenumeratoraccessor-m-szname.md)|Název zdroje dat nebo enumerátor.|  
|[m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)|Řetězec, který má předat [IParseDisplayName](http://msdn.microsoft.com/library/windows/desktop/ms680604) získat Přezdívka pro zdroj dat nebo enumerátor.|  
  
## <a name="remarks"></a>Poznámky  
 Tato sada řádků se skládá z zdroje dat a výčty viditelné z aktuální enumerátor.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)