---
title: FOPEN_MAX –, _SYS_OPEN – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _SYS_OPEN
- FOPEN_MAX
dev_langs:
- C++
helpviewer_keywords:
- SYS_OPEN constant
- _SYS_OPEN constant
- FOPEN_MAX constant
- files [C++], maximum open
- maximum number of files
- open files, maximum
ms.assetid: 39cf5196-250a-459d-ae90-ce3d99f79039
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3f834dd94ab67ade81969de76eef33bf139299f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="fopenmax-sysopen"></a>FOPEN_MAX, _SYS_OPEN
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <stdio.h>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Toto je maximální počet souborů, které lze otevřít současně. `FOPEN_MAX` je název ANSI kompatibilní. `_SYS_OPEN` slouží k zajištění kompatibility s existujícího kódu.  
  
## <a name="see-also"></a>Viz také  
 [Globální konstanty](../c-runtime-library/global-constants.md)