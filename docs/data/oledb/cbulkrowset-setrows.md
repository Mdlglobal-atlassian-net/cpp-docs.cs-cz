---
title: CBulkRowset::SetRows | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CBulkRowset.SetRows
- CBulkRowset::SetRows
- CBulkRowset<TAccessor>.SetRows
- ATL.CBulkRowset<TAccessor>.SetRows
- CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset::SetRows
- CBulkRowset.SetRows
- SetRows
dev_langs:
- C++
helpviewer_keywords:
- SetRows method
ms.assetid: 7e92312a-bfd0-4c24-a799-62bef663f28e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8cfbe5abc559291978bb54fe0d30ea0c081cdf82
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="cbulkrowsetsetrows"></a>CBulkRowset::SetRows
Nastaví počet popisovačů řádků, které jsou načítána pro každé volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      void SetRows(DBROWCOUNT nRows) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nRows`  
 [v] Novou velikost sady řádků (počet řádků).  
  
## <a name="remarks"></a>Poznámky  
 Při volání této funkce, musí být před otevřením sady řádků.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CBulkRowset – třída](../../data/oledb/cbulkrowset-class.md)