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
ms.openlocfilehash: 26a5b349836b7c9b08a66d4df8f3d2bedbe5b63f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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