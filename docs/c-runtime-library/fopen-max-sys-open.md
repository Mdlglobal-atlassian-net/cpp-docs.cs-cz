---
title: "FOPEN_MAX –, _SYS_OPEN – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _SYS_OPEN
- FOPEN_MAX
dev_langs: C++
helpviewer_keywords:
- SYS_OPEN constant
- _SYS_OPEN constant
- FOPEN_MAX constant
- files [C++], maximum open
- maximum number of files
- open files, maximum
ms.assetid: 39cf5196-250a-459d-ae90-ce3d99f79039
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4078d13348c56810a42d3c6b3df17f9058f7b27d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fopenmax-sysopen"></a>FOPEN_MAX, _SYS_OPEN
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <stdio.h>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Toto je maximální počet souborů, které lze otevřít současně. `FOPEN_MAX`je název ANSI kompatibilní. `_SYS_OPEN`slouží k zajištění kompatibility s existujícího kódu.  
  
## <a name="see-also"></a>Viz také  
 [Globální konstanty](../c-runtime-library/global-constants.md)