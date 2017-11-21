---
title: "&lt;nové&gt; – definice TypeDef | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
caps.latest.revision: "7"
manager: ghogen
ms.openlocfilehash: e23ea06002dc840997a0e7202f581cd81ef407c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltnewgt-typedefs"></a>&lt;nové&gt; – definice TypeDef
||  
|-|  
|[new_handler](#new_handler)|  
  
##  <a name="new_handler"></a>new_handler  
 Body typu vhodný pro funkci použít jako novou obslužnou rutinu.  
  
```
typedef void (*new_handler)();
```  
  
### <a name="remarks"></a>Poznámky  
 Tento typ obslužné rutiny funkce volá **operatornew** nebo `operator new[]` při nemůže splnit žádost o další úložiště.  
  
### <a name="example"></a>Příklad  
  V tématu [set_new_handler –](../standard-library/new-functions.md#set_new_handler) pro příklad použití `new_handler` jako návratová hodnota.  
  
## <a name="see-also"></a>Viz také  
 [\<Nový >](../standard-library/new.md)



