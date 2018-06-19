---
title: Kompilátoru (úroveň 3) upozornění C4290 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4290
dev_langs:
- C++
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f03d35e1a3756979d8936647255e2b65afef56d9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289890"
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