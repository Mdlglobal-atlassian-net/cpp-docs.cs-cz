---
title: END_ACCESSOR_MAP | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- END_ACCESSOR_MAP
dev_langs:
- C++
helpviewer_keywords:
- END_ACCESSOR_MAP macro
ms.assetid: ede813c7-46c9-48a6-aa1a-8ebf38e92023
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 139fcf788449a8cd1d23e2aa85691f8d0e8c3da7
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="endaccessormap"></a>END_ACCESSOR_MAP
Označuje konec položek mapování přistupujícího objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
END_ACCESSOR_MAP()  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Pro více přístupových objektů pro sadu řádků, je třeba zadat `BEGIN_ACCESSOR_MAP` a použít `BEGIN_ACCESSOR` makro pro každé jednotlivé přistupujícího objektu. `BEGIN_ACCESSOR` Makro byla dokončena s `END_ACCESSOR` makro. `BEGIN_ACCESSOR_MAP` Makro byla dokončena s `END_ACCESSOR_MAP` makro.  
  
## <a name="example"></a>Příklad  
 V tématu [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)