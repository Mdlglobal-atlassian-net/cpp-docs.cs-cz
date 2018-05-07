---
title: C2381 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2381
dev_langs:
- C++
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bd5f5edcf95144333524c41b803c24b728a621f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2381"></a>C2381 chyby kompilátoru
'function': předefinování; __declspec(noreturn) se liší.  
  
 Funkci byl deklarován a pak definované ale jako definice použitá [noreturn](../../cpp/noreturn.md) `__declspec` modifikátor. Použití `noreturn` předefinování funkce se považuje za; deklarace a definice muset ke shodě o použití `noreturn`.  
  
 Následující ukázka generuje C2381:  
  
```  
// C2381.cpp  
// compile with: /c  
void f1();  
void __declspec(noreturn) f1() {}   // C2381  
void __declspec(noreturn) f2() {}   // OK  
```