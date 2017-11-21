---
title: "spawn – konstanty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _P_NOWAIT
- _P_OVERLAY
- _P_WAIT
- _P_DETACH
- _P_NOWAITO
dev_langs: C++
helpviewer_keywords:
- _P_OVERLAY constant
- P_DETACH constant
- P_OVERLAY constant
- P_NOWAIT constant
- _P_DETACH constant
- _P_NOWAIT constant
- _P_NOWAITO constant
- P_NOWAITO constant
- spawn constants
- P_WAIT constant
- _P_WAIT constant
ms.assetid: e0533e88-d362-46fc-b53c-5f193226d879
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8f5f30cbf6598e4ac8d88652a6a842dcd6209273
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="spawn-constants"></a>spawn – konstanty
## <a name="syntax"></a>Syntaxe  
  
```  
#include <process.h>  
```  
  
## <a name="remarks"></a>Poznámky  
 `mode` Argument určuje akci provedenou volající proces před a během operace spawn. Následující hodnoty pro `mode` je možné:  
  
|Konstanta|Význam|  
|--------------|-------------|  
|`_P_OVERLAY`|Překryvy volání proces s nový proces, zničení volání procesu (stejné jako ovlivňuje `_exec` volání).|  
|`_P_WAIT`|Pozastaví volající vlákno až do dokončení provádění nový proces (synchronní `_spawn`).|  
|`_P_NOWAIT`, `_P_NOWAITO`|Bude pokračovat v provádění volající proces souběžně nový proces (asynchronní `_spawn`).|  
|`_P_DETACH`|Bude pokračovat v provádění volání procesu; Nový proces běží na pozadí bez přístupu na konzole nebo klávesnice. Volání `_cwait` proti nový proces se nezdaří. Jedná se asynchronní `_spawn`.|  
  
## <a name="see-also"></a>Viz také  
 [_spawn, _wspawn – funkce](../c-runtime-library/spawn-wspawn-functions.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)