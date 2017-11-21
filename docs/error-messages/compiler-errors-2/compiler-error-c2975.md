---
title: "C2975 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2975
dev_langs: C++
helpviewer_keywords: C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 65644cc13629481941ffdd8676e51311c665f106
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2017
---
# <a name="compiler-error-c2975"></a>C2975 chyby kompilátoru

> '*argument*': argument neplatný šablony pro '*typ*', očekávána konstantní výraz kompilace

Argument šablony neodpovídá deklaraci šablony; konstantní výraz by měl být použit v lomené závorky. Jako šablona skutečné argumenty nejsou povoleny proměnné. Zkontrolujte definici šablony najít správný typy.

## <a name="example"></a>Příklad

Následující ukázka generuje C2975 a také ukazuje správné použití:

```cpp
// C2975.cpp
template<int I>
class X {};

int main() {
   int i = 4, j = 2;
   X<i + j> x1;   // C2975
   X<6> x2;   // OK
}
```

C2975 také nastat, když použijete &#95; &#95; Řádek &#95; &#95; jako konstanta kompilaci s [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md). Jedno řešení by mohla být kompilovat s [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) místo **/ZI**.

```cpp
// C2975b.cpp
// compile with: /ZI
// processor: x86
template<long line>
void test(void) {}

int main() {
   test<__LINE__>();   // C2975
}
```