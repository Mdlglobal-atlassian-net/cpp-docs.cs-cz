---
title: "Mapování konstant a globálních proměnných | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _tenviron
- _TEOF
- _tfinddata_t
dev_langs: C++
helpviewer_keywords:
- tfinddatat function
- tenviron function
- TEOF type
- _TEOF type
- generic-text mappings
- _tenviron function
- _tfinddata_t function
ms.assetid: 3af4fd3e-9ed5-4ed9-96fd-7031e5126fd1
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 55c388ddddb5fd774afb6c4e84d6a96a4c38bebe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="constant-and-global-variable-mappings"></a>Mapování konstant a globálních proměnných
Tyto obecného textu konstanta, globální proměnné a mapování typu standard jsou definovány v Tchar –. H a závisí na tom, zda konstanta `_UNICODE` nebo `_MBCS` byla definována v programu.  
  
### <a name="generic-text-constant-and-global-variable-mappings"></a>Mapování obecného textu konstant a globálních proměnných  
  
|Obecné textové – název objektu|SBCS (_UNICODE, není definována _MBCS)|_MBCS definováno|_UNICODE definováno|  
|----------------------------------|--------------------------------------------|--------------------|-----------------------|  
|`_TEOF`|`EOF`|`EOF`|`WEOF`|  
|`_tenviron`|`_environ`|`_environ`|`_wenviron`|  
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|  
  
## <a name="see-also"></a>Viz také  
 [Mapování obecného textu](../c-runtime-library/generic-text-mappings.md)   
 [Mapování datového typu](../c-runtime-library/data-type-mappings.md)   
 [Mapování rutiny](../c-runtime-library/routine-mappings.md)   
 [Ukázka programu obecného textu](../c-runtime-library/a-sample-generic-text-program.md)   
 [Použití mapování obecného textu](../c-runtime-library/using-generic-text-mappings.md)