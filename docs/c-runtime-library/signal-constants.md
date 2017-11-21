---
title: "Signal – konstanty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SIGTERM
- SIGFPE
- SIGABRT
- SIGILL
- SIGINT
- SIGSEGV
dev_langs: C++
helpviewer_keywords:
- SIGTERM constant
- SIGABRT constant
- SIGSEGV constant
- SIGFPE constant
- SIGINT constant
- signal constants
- SIGILL constant
ms.assetid: a3b39281-dae7-4e44-8d68-e6a610c669dd
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fddb279acfbb6d8841ac17a27cd43de205dc9dbc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="signal-constants"></a>signal – konstanty
## <a name="syntax"></a>Syntaxe  
  
```  
#include <signal.h>  
```  
  
## <a name="remarks"></a>Poznámky  
 `sig` Argument musí být jeden z manifestu konstanty uvedené níže (definovaná v SIGNÁL. H).  
  
 `SIGABRT`  
 Abnormální ukončení. Výchozí akce ukončí volací program s ukončovacím kódem 3.  
  
 `SIGABRT_COMPAT`  
 Stejné jako sigabrt –. Pro kompatibilitu s jinými platformami.  
  
 `SIGFPE`  
 Chyba s plovoucí desetinnou čárkou, jako jsou například přetečení, dělení nulou či neplatná operace. Výchozí akce ukončí volací program.  
  
 `SIGILL`  
 Neplatná instrukce. Výchozí akce ukončí volací program.  
  
 `SIGINT`  
 CTRL + C přerušení. Výchozí akce ukončí volací program s ukončovacím kódem 3.  
  
 `SIGSEGV`  
 Neplatné úložiště přístup. Výchozí akce ukončí volací program.  
  
 `SIGTERM`  
 Ukončení požadavek odeslaný program. Výchozí akce ukončí volací program s ukončovacím kódem 3.  
  
 `SIG_ERR`  
 Návratový typ z signál, který chybu došlo k chybě.  
  
## <a name="see-also"></a>Viz také  
 [signál](../c-runtime-library/reference/signal.md)   
 [vyvolat](../c-runtime-library/reference/raise.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)