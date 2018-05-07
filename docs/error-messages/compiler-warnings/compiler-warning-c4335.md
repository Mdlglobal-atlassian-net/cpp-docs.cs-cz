---
title: C4335 upozornění kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4335
dev_langs:
- C++
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: adb8a7b484ce0946f385c3b2a8669ba1b5ccf0d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4335"></a>C4335 upozornění kompilátoru
Formát souboru Mac zjistil: prosím převést zdrojový soubor formátu DOS nebo UNIX  
  
 Znak ukončení řádku prvního řádku zdrojového souboru je Macintosh styl (\r) a UNIX (\n) nebo DOS (\r\n).  
  
 Jako errror vždy se objeví toto upozornění.  V tématu [upozornění](../../preprocessor/warning.md) – Direktiva pragma pro informace o tom, jak zakázat toto upozornění.  Navíc se objeví toto upozornění pouze jednou za kompilace. Proto pokud existuje více `#include` direktivy, které určují soubory ve formátu Macintosh, C4335 bude vystavit pouze jednou.  
  
 Jedním ze způsobů pro vygenerování souborů ve formátu Macintosh je pomocí **rozšířené možnosti ukládání** (na **souboru** nabídky) v sadě Visual Studio.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4335.  
  
```  
// C4335 expected  
#include "c4335.h"   // assume both include files are in Macintosh format  
#include "c4335_2.h"  
```