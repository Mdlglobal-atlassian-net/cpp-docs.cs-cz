---
title: "C2653 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2653
dev_langs:
- C++
helpviewer_keywords:
- C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f18e3d6210c5d9b9aba4fdfaab296a01d32b6d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2653"></a>C2653 chyby kompilátoru

> '*identifikátor*': není třída nebo obor názvů

Syntaxe jazyka vyžaduje třídy, struktury, sjednocení nebo zde název oboru názvů.

Této chybě může dojít, pokud použijete název, který nebyl deklarován jako třídy, struktury, sjednocení nebo obor názvů před operátor rozsahu. Chcete-li tento problém vyřešit, deklarovat název nebo obsahovat záhlaví, který deklaruje název, než bude použit.

C2653 je také možné, pokud se pokusíte definovat *složené obor názvů*, obor názvů, který obsahuje jeden nebo více názvy vnořené oboru názvů. Složené obor názvů, který definice nejsou povoleny v jazyce C++ před C ++ 17. Složené obory názvů jsou podporované počínaje Visual Studio 2015 Update 3, když zadáte [/std: c ++ nejnovější](../../build/reference/std-specify-language-standard-version.md) – možnost kompilátoru. Od verze Visual C++ 2017 verze 15,5, kompilátor podporuje složené obor názvů definice při [/std: c ++ 17](../../build/reference/std-specify-language-standard-version.md) je zadána možnost.

## <a name="examples"></a>Příklady

Tato ukázka generuje C2653, protože název oboru je použít, ale není deklarován. Kompilátor očekává třídy, struktury, sjednocení nebo název oboru názvů před operátor rozsahu (:).

```cpp
// C2653.cpp
// compile with: /c
class yy {
   void func1(int i);
};

void xx::func1(int m) {}   // C2653, xx is not declared
void yy::func1(int m) {}   // OK
```

V kódu, který není zkompilovaném pro C ++ 17 nebo novější standardů musí vnořené obory názvů pomocí deklarace oboru názvů explicitní na každou úroveň vnoření:

```cpp
// C2653b.cpp
namespace a::b {int i;}   // C2653 prior to Visual C++ 2015 Update 3,
                          // C2429 thereafter. Use /std:c++17 or /std:c++latest to fix.

namespace a {             // Use this form for compliant code under /std:c++14 (the default)
   namespace b {          // or when using compilers before Visual Studio 2015 update 3.
      int i;
   }
}

int main() {
   a::b::i = 2;
}
```
