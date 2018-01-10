---
title: "_WAIT_CHILD –, _WAIT_GRANDCHILD – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _WAIT_GRANDCHILD
- WAIT_CHILD
- WAIT_GRANDCHILD
- _WAIT_CHILD
dev_langs: C++
helpviewer_keywords:
- WAIT_CHILD constant
- WAIT_GRANDCHILD constant
- _WAIT_CHILD constant
- _WAIT_GRANDCHILD constant
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1ac83e22e906a4e885860ec2254b2b732e31d38a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="waitchild-waitgrandchild"></a>_WAIT_CHILD, _WAIT_GRANDCHILD
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <process.h>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 `_cwait` Funkce lze jakýkoli proces čekání na jiný proces (Pokud je ID procesu je znám). Argument akce může být jedna z následujících hodnot:  
  
|Konstanta|Význam|  
|--------------|-------------|  
|`_WAIT_CHILD`|Volání proces čeká na zadaný nový proces ukončí.|  
|`_WAIT_GRANDCHILD`|Volání proces počká až zadaný nový proces a všechny procesy vytvořenými službou tento nový proces ukončete.|  
  
## <a name="see-also"></a>Viz také  
 [_cwait –](../c-runtime-library/reference/cwait.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)