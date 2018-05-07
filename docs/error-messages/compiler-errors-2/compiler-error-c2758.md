---
title: C2758 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2758
dev_langs:
- C++
helpviewer_keywords:
- C2758
ms.assetid: 1d273034-194c-4926-9869-142d1b219cbe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 34cce7840f888a4377440299a4dc5ac38ee6a1d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2758"></a>C2758 chyby kompilátoru
"člen": členem typ odkazu musí být inicializován.  
  
 Chyba kompilátoru C2758 dojde, pokud nebude členem odkaz v seznamu inicializátoru konstruktoru se inicializovat. Kompilátor zanechává člen není definovaná. Odkazovat člen, proměnné musí inicializovat při deklarován nebo mít hodnotu v seznamu inicializace konstruktoru.  
  
 Následující ukázka generuje C2758:  
  
```  
// C2758.cpp  
// Compile by using: cl /W3 /c C2758.cpp  
struct A {  
   const int i;  
  
   A(int n) { };   // C2758  
   // try the following line instead  
   // A(int n) : i{n} {};  
};  
```