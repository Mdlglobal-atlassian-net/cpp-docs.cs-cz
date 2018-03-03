---
title: "fseek, _lseek – konstanty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SEEK_END
- SEEK_SET
- SEEK_CUR
dev_langs:
- C++
helpviewer_keywords:
- SEEK_SET constant
- SEEK_END constant
- SEEK_CUR constant
ms.assetid: 9deeb13e-5aa3-4c33-80d8-721c80a4de9d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4ccdee5d17b95772072f95a046e6e3c4d9a30e0e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fseek-lseek-constants"></a>fseek, _lseek – konstanty
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <stdio.h>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 *Původu* argument určuje počáteční pozici a může být jedna z následujících konstant manifestu:  
  
|Konstanta|Význam|  
|--------------|-------------|  
|`SEEK_END`|Konec souboru|  
|`SEEK_CUR`|Aktuální pozici ukazatele souboru|  
|`SEEK_SET`|Začátek souboru|  
  
## <a name="see-also"></a>Viz také  
 [fseek, _fseeki64 –](../c-runtime-library/reference/fseek-fseeki64.md)   
 [_lseek –, _lseeki64 –](../c-runtime-library/reference/lseek-lseeki64.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)