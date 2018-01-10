---
title: "C4335 upozornění kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4335
dev_langs: C++
helpviewer_keywords: C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ea0a981c00a1941c3004ac820edbcbbbf0776c4c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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