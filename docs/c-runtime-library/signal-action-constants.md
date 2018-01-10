---
title: "Signal – konstanty akce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SIG_IGN
- SIG_DFL
dev_langs: C++
helpviewer_keywords:
- signal action constants
- SIG_IGN constant
- SIG_DFL constant
ms.assetid: c3cb4f15-d39e-4d9d-84f9-0d33e3eb5993
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 256f11d3f8daa8a00e70e24aa19c31b71413c13c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="signal-action-constants"></a>signal – konstanty akce
Akce prováděné při doručení signál přerušení závisí na hodnotu `func`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <signal.h>  
```  
  
## <a name="remarks"></a>Poznámky  
 `func` Argument musí být buď adresu funkce nebo jeden z manifestu konstanty uvedené níže a definované v SIGNÁL. H.  
  
 `SIG_DFL`  
 Použije systém výchozí odpověď. Pokud volací program používá vstupně-výstupní datový proud, nejsou vyprázdněna vytvořen běhové knihovny vyrovnávací paměti.  
  
 `SIG_IGN`  
 Ignoruje signál přerušení. Tato hodnota má být poskytnut nikdy pro `SIGFPE`, protože je ponechán s plovoucí desetinnou čárkou stav procesu definován.  
  
 `SIG_SGE`  
 Označuje, že došlo k chybě v signál.  
  
 `SIG_ACK`  
 Označuje, že bylo přijato potvrzení.  
  
 `SIG_ERR`  
 Návratový typ z signál, který chybu došlo k chybě.  
  
## <a name="see-also"></a>Viz také  
 [signál](../c-runtime-library/reference/signal.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)