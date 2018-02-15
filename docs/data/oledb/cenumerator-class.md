---
title: "CEnumerator – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
ms.openlocfilehash: f15ed0f0963987dab0c6170cc9a05bf4c28abdce
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
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