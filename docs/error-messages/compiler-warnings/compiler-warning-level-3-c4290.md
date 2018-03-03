---
title: "Kompilátoru (úroveň 3) upozornění C4290 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4290
dev_langs:
- C++
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f70a278cb3e660e89e1aba067cab9c20aacf8f62
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4290"></a>C4290 kompilátoru upozornění (úroveň 3)
Specifikace výjimek C++ ignorovat kromě Chcete-li určit funkce není __declspec(nothrow)  
  
 Funkce je deklarovaná pomocí specifikace výjimek, které přijímá Visual C++, ale neimplementuje. Kód s výjimkou, které specifikace, které ignorují během kompilace může třeba zopakovat a propojené být znovu použít v budoucích verzích podporu specifikace výjimek.  
  
 Další informace najdete v tématu [specifikace výjimek (throw)](../../cpp/exception-specifications-throw-cpp.md) .  
  
 Toto upozornění můžete vyhnout použitím [upozornění](../../preprocessor/warning.md) – Direktiva pragma:  
  
```  
#pragma warning( disable : 4290 )  
```  
  
 Následující ukázka kódu generuje C4290:  
  
```  
// C4290.cpp  
// compile with: /EHs /W3 /c  
void f1(void) throw(int) {}   // C4290  
  
// OK  
void f2(void) throw() {}  
void f3(void) throw(...) {}  
```