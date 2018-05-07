---
title: C2021 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2021
dev_langs:
- C++
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae1c3640b4fbe5b1473c2e678406321f5533e586
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2021"></a>C2021 chyby kompilátoru
očekávala se hodnota exponentu, není znak  
  
 Znak použitý jako exponent s plovoucí desetinnou čárkou konstanta není platné číslo. Nezapomeňte použít exponentem, která je v dosahu.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2021:  
  
```  
// C2021.cpp  
float test1=1.175494351E;   // C2021  
```  
  
## <a name="example"></a>Příklad  
 Možná řešení:  
  
```  
// C2021b.cpp  
// compile with: /c  
float test2=1.175494351E8;  
```