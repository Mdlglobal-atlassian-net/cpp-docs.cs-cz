---
title: "CEnumerator – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CEnumerator
dev_langs:
- C++
helpviewer_keywords:
- CEnumerator class
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d0ac9fe73b2d8b37e345ddcf602dd98316eedf46
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="cenumerator-class"></a>CEnumerator – třída
Používá objekt enumerator OLE DB, který zveřejňuje [ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx) rozhraní vrátí sadu řádků, které popisují všechny zdroje dat a výčty.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CEnumerator :   
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>  
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Najít](../../data/oledb/cenumerator-find.md)|Hledání prostřednictvím (zdroje dat) dostupných zprostředkovatelů vyhledávání pro jednu se zadaným názvem.|  
|[GetMoniker](../../data/oledb/cenumerator-getmoniker.md)|Načte `IMoniker` rozhraní pro záznam na aktuální záznam.|  
|[Open](../../data/oledb/cenumerator-open.md)|Otevře enumerátor.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete získat **ISourcesRowset** data nepřímo z této třídy.  
  
## <a name="requirements"></a>Požadavky  
 **Header:**atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [DBViewer](../../visual-cpp-samples.md)   
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)