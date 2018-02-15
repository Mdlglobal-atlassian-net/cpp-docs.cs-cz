---
title: "CArrayRowset – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CArrayRowset<TAccessor>
- ATL.CArrayRowset
- CArrayRowset
- ATL::CArrayRowset
- ATL::CArrayRowset<TAccessor>
dev_langs:
- C++
helpviewer_keywords:
- CArrayRowset class
ms.assetid: 511427e1-73ca-4fd8-9ba1-ae9463557cb6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ea9df3ae818a76f553b18ce885ee4863da6b87e3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="carrayrowset-class"></a>CArrayRowset – třída
Přístupy prvky sady řádků pomocí syntaxe pole.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template < class TAccessor >  
class CArrayRowset :   
   public CVirtualBuffer <TAccessor>,   
   protected CBulkRowset <TAccessor>  
```  
  
#### <a name="parameters"></a>Parametry  
 `TAccessor`  
 Typ třídy přistupujícího objektu, která chcete používat sadu řádků.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CArrayRowset](../../data/oledb/carrayrowset-carrayrowset.md)|Konstruktor|  
|[Snímek](../../data/oledb/carrayrowset-snapshot.md)|Načte celý řádků do paměti.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[Operator&#91;&#93;](../../data/oledb/carrayrowset-operator.md)|Přístup k elementu sady řádků.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[CArrayRowset::m_nRowsRead](../../data/oledb/carrayrowset-m-nrowsread.md)|Počet řádků, které jsou již pro čtení.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace šablony příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CRowset – třída](../../data/oledb/crowset-class.md)