---
title: C2812 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2812
dev_langs:
- C++
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28d46b0f9744f192d677d7b2df27b67e734de1b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2812"></a>C2812 chyby kompilátoru
\#Import není podporován s volbou/CLR: pure a/CLR: safe  
  
 **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
 [#import – direktiva](../../preprocessor/hash-import-directive-cpp.md) není podporovaný s **/CLR: pure** a **/CLR: safe** protože `#import` vyžaduje použití nativního kompilátoru podpory knihovny.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2812.  
  
```  
// C2812.cpp  
// compile with: /clr:pure /c  
#import "importlib.tlb"   // C2812  
```