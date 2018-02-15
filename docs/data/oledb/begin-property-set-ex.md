---
title: BEGIN_PROPERTY_SET_EX | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BEGIN_PROPERTY_SET_EX
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_PROPERTY_SET_EX macro
ms.assetid: c95e7fab-edce-47b8-b282-200e53a2ea8a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bc3738ca9fc03014b68cc47cadad32ac4865b0d1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="beginpropertysetex"></a>BEGIN_PROPERTY_SET_EX
Značky začátku vlastnost nastavena pro vlastnost, nastavte mapy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
BEGIN_PROPERTY_SET_EX(guid  
, flags )  
```  
  
#### <a name="parameters"></a>Parametry  
 `guid`  
 [v] Vlastnost identifikátor GUID.  
  
 `flags`  
 [v] **UPROPSET_HIDDEN** pro všechny sady vlastností nechcete, aby ke zveřejnění, nebo **UPROPSET_PASSTHROUGH** zprostředkovatele vystavení vlastnosti definované mimo obor zprostředkovatele.  
  
## <a name="example"></a>Příklad  
 V tématu [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Makra pro šablony zprostředkovatele technologie OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)