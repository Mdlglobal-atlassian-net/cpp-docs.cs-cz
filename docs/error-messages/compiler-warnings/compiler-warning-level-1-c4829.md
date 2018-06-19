---
title: Kompilátoru (úroveň 1) upozornění C4829 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4829
dev_langs:
- C++
helpviewer_keywords:
- C4829
ms.assetid: 4ffabe2b-2ddc-4c52-8564-d1355c93cfa6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c27ca268a3c873474cd4ed79a2b843642087c34
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286536"
---
# <a name="compiler-warning-level-1-c4829"></a>C4829 kompilátoru upozornění (úroveň 1)
Může být nesprávné parametry hlavní funkce. Vezměte v úvahu ' intmain (Platform::Array\<Platform::String ^ > ^ argv –).  
  
 Určité funkce, jako jsou hlavní, nelze zpracovat referenční parametry typu. Při kompilaci bude úspěšné, bude výsledný obraz pravděpodobně nejde spustit.  
  
 Následující ukázka generuje C4829:  
  
```  
// C4829.cpp  
// compile by using: cl /EHsc /ZW /W4 /c C4829.cpp  
int main(Platform::String ^ s) {}   // C4829  
  
```