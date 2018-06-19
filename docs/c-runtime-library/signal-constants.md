---
title: Signal – konstanty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- SIGTERM
- SIGFPE
- SIGABRT
- SIGILL
- SIGINT
- SIGSEGV
dev_langs:
- C++
helpviewer_keywords:
- SIGTERM constant
- SIGABRT constant
- SIGSEGV constant
- SIGFPE constant
- SIGINT constant
- signal constants
- SIGILL constant
ms.assetid: a3b39281-dae7-4e44-8d68-e6a610c669dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 279f4beb3b550f672ac3950c31f3653ca1f00ba2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409355"
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
 [Signál](../c-runtime-library/reference/signal.md)   
 [Vyvolat](../c-runtime-library/reference/raise.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)