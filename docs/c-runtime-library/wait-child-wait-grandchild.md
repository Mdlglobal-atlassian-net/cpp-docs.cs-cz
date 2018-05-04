---
title: _WAIT_CHILD –, _WAIT_GRANDCHILD – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _WAIT_GRANDCHILD
- WAIT_CHILD
- WAIT_GRANDCHILD
- _WAIT_CHILD
dev_langs:
- C++
helpviewer_keywords:
- WAIT_CHILD constant
- WAIT_GRANDCHILD constant
- _WAIT_CHILD constant
- _WAIT_GRANDCHILD constant
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84e0f195bebd43ced767f05a7c6073a6d6e9db61
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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