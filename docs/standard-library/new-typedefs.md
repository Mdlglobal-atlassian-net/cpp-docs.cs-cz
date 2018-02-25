---
title: "&lt;nové&gt; – definice TypeDef | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: cbcc542095ad8b75bbe632f741f43206e436b5e4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltnewgt-typedefs"></a>&lt;nové&gt; – definice TypeDef
||  
|-|  
|[new_handler](#new_handler)|  
  
##  <a name="new_handler"></a>  new_handler  
 Body typu vhodný pro funkci použít jako novou obslužnou rutinu.  
  
```
typedef void (*new_handler)();
```  
  
### <a name="remarks"></a>Poznámky  
 Tento typ obslužné rutiny funkce volá **operatornew** nebo `operator new[]` při nemůže splnit žádost o další úložiště.  
  
### <a name="example"></a>Příklad  
  V tématu [set_new_handler –](../standard-library/new-functions.md#set_new_handler) pro příklad použití `new_handler` jako návratová hodnota.  
  
## <a name="see-also"></a>Viz také  
 [\<new>](../standard-library/new.md)



