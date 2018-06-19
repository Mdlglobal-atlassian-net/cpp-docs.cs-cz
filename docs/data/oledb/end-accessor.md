---
title: END_ACCESSOR | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- END_ACCESSOR
dev_langs:
- C++
helpviewer_keywords:
- END_ACCESSOR macro
ms.assetid: 26f74167-68c4-4909-a474-73dc7ebc9542
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f7bab52df0ed05886933a3df827fae5198651b39
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099235"
---
# <a name="endaccessor"></a>END_ACCESSOR
Označuje konec položku přistupujícího objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
END_ACCESSOR()  
  
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
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)