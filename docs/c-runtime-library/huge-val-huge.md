---
title: HUGE_VAL –, _HUGE – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _HUGE
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _HUGE
- HUGE_VAL
dev_langs:
- C++
helpviewer_keywords:
- _HUGE constant
- HUGE_VAL constant
- double value
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2d763b8c5379223ddacb8077c463efa0b91acfa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="hugeval-huge"></a>HUGE_VAL, _HUGE
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <math.h>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 `HUGE_VAL` je největší reprezentovat dvojitou hodnotu. Tato hodnota je vrácený mnoho běhu matematické funkce, když dojde k chybě. Pro některé funkce-`HUGE_VAL` je vrácen. `HUGE_VAL` je definován jako `_HUGE`, ale běhu matematické funkce vrátit `HUGE_VAL`. Byste měli použít také `HUGE_VAL` ve vašem kódu konzistence.  
  
## <a name="see-also"></a>Viz také  
 [Globální konstanty](../c-runtime-library/global-constants.md)