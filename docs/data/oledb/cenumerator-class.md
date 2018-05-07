---
title: CEnumerator – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CEnumerator
dev_langs:
- C++
helpviewer_keywords:
- CEnumerator class
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2b7e390212da53f85cb50dd5bb151ea6740784b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
|[Otevřete](../../data/oledb/cenumerator-open.md)|Otevře enumerátor.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete získat **ISourcesRowset** data nepřímo z této třídy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [DBViewer](../../visual-cpp-samples.md)   
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)