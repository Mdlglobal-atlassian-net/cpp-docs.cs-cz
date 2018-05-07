---
title: Kompilátoru (úroveň 1) upozornění C4028 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4028
dev_langs:
- C++
helpviewer_keywords:
- C4028
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c96abd732a00e5b37b48be8c3053cbfbb8c37c37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4028"></a>C4028 kompilátoru upozornění (úroveň 1)
formální parametr "číslo" liší od deklarace  
  
 Typ formálního parametru s odpovídající parametr v deklaraci nesouhlasí. Typ v původní deklaraci se používá.  
  
 Toto upozornění je platná pouze pro zdrojový kód C.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4028.  
  
```  
// C4028.c  
// compile with: /W1 /Za  
void f(int , ...);  
void f(int i, int j) {}   // C4028  
  
void g(int , int);  
void g(int i, int j) {}   // OK  
  
int main() {}  
```