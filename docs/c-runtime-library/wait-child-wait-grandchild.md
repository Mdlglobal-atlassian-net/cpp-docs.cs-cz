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
ms.openlocfilehash: 1e5e3aa48f0184730a7860ea055d9b233b4ac708
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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