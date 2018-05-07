---
title: CDynamicAccessor::GetBlobHandling | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicAccessor.GetBlobHandling
- CDynamicAccessor::GetBlobHandling
- ATL::CDynamicAccessor::GetBlobHandling
- GetBlobHandling
- CDynamicAccessor.GetBlobHandling
dev_langs:
- C++
helpviewer_keywords:
- GetBlobHandling method
ms.assetid: bbc6dda6-e132-42a3-980d-24e455cbe456
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 51cc3dedb848058257861f901a46e0377115007d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicaccessorgetblobhandling"></a>CDynamicAccessor::GetBlobHandling
Načte objekt BLOB zpracování hodnotu pro aktuální řádek.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
const DBBLOBHANDLINGENUM GetBlobHandling() const;  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Vrátí objekt BLOB zpracování hodnotu `eBlobHandling` jako nastavte podle [setblobhandling –](../../data/oledb/cdynamicaccessor-setblobhandling.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)