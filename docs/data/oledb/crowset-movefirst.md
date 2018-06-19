---
title: CRowset::MoveFirst | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowset<TAccessor>::MoveFirst
- ATL::CRowset::MoveFirst
- CRowset<TAccessor>.MoveFirst
- CRowset::MoveFirst
- CRowset.MoveFirst
- ATL.CRowset.MoveFirst
- ATL.CRowset<TAccessor>.MoveFirst
- ATL::CRowset<TAccessor>::MoveFirst
dev_langs:
- C++
helpviewer_keywords:
- MoveFirst method
ms.assetid: a17c0799-ead9-4d85-9a1d-8b17188d01e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 811e2cdc18711c85cbb2a43e555a273bf3f50d81
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091781"
---
# <a name="crowsetmovefirst"></a>CRowset::MoveFirst
Posune kurzor na počáteční pozici a načte počáteční řádek.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT MoveFirst() throw();  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Volání [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx) aby přemístil další načítání umístění na počáteční pozici (pozice, který byl další načítání umístění sady řádků v okamžiku vytvoření) a načte počáteční řádek.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CRowset – třída](../../data/oledb/crowset-class.md)   
 [CRowset::MoveNext](../../data/oledb/crowset-movenext.md)   
 [CRowset::MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)   
 [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx)