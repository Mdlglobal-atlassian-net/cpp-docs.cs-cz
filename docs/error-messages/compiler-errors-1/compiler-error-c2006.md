---
title: C2006 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2006
dev_langs:
- C++
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 93880e7d767de3101cd7a292af5fa2874cae86bf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33165568"
---
# <a name="compiler-error-c2006"></a>C2006 chyby kompilátoru
"směrnice" očekávaný název souboru, nalezen 'tokenu.  
  
 Direktivy jako [#include](../../preprocessor/hash-include-directive-c-cpp.md) nebo [#import](../../preprocessor/hash-import-directive-cpp.md) vyžadovat název souboru. Chcete-li vyřešit chyby, ujistěte se, *tokenu* je platný název souboru. Navíc uveďte název souboru do dvojitých uvozovek nebo lomené závorky.  
  
 Následující ukázka generuje C2006:  
  
```  
// C2006.cpp  
#include stdio.h   // C2006  
```  
  
 Možná řešení:  
  
```  
// C2006b.cpp  
// compile with: /c  
#include <stdio.h>  
```