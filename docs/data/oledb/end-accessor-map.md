---
title: END_ACCESSOR_MAP | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: END_ACCESSOR_MAP
dev_langs: C++
helpviewer_keywords: END_ACCESSOR_MAP macro
ms.assetid: ede813c7-46c9-48a6-aa1a-8ebf38e92023
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7cbad12a88374b3f6aa23f54f92ed55f0d827ef1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="endaccessormap"></a>END_ACCESSOR_MAP
Označuje konec položek mapování přistupujícího objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
END_ACCESSOR_MAP( )  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Pro více přístupových objektů pro sadu řádků, je třeba zadat `BEGIN_ACCESSOR_MAP` a použít `BEGIN_ACCESSOR` makro pro každé jednotlivé přistupujícího objektu. `BEGIN_ACCESSOR` Makro byla dokončena s `END_ACCESSOR` makro. `BEGIN_ACCESSOR_MAP` Makro byla dokončena s `END_ACCESSOR_MAP` makro.  
  
## <a name="example"></a>Příklad  
 V tématu [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR_MAP –](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)