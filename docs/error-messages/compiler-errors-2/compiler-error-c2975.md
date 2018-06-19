---
title: C2975 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2975
dev_langs:
- C++
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53cb020dc0d456f10b7cfbae82a16b2ebe5fda6b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246980"
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

C2975 také nastane, když používáte &#95; &#95;řádku&#95; &#95; jako konstanta kompilaci s [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md). Jedno řešení by mohla být kompilovat s [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) místo **/ZI**.

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