---
title: Chyba kompilátoru C3821
ms.date: 11/04/2016
f1_keywords:
- C3821
helpviewer_keywords:
- C3821
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
ms.openlocfilehash: 25023277258d33ab77bde18f6cdfabc862f50a63
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741739"
---
# <a name="compiler-error-c3821"></a>Chyba kompilátoru C3821

' function ': spravovaný typ nebo funkci nelze použít v nespravované funkci

Funkce s vloženým sestavením nebo [setjmp](../../c-runtime-library/reference/setjmp.md) nemůže obsahovat typy hodnot ani spravované třídy. Chcete-li tuto chybu opravit, odeberte vložené sestavení a `setjmp` nebo odeberte spravované objekty.

K C3821 může také dojít, pokud se pokusíte použít automatické úložiště ve funkci vararg.  Další informace naleznete v tématu [proměnné seznamy argumentů (...) (C++/CLI)](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md) a [ C++ sémantika zásobníku pro odkazové typy](../../dotnet/cpp-stack-semantics-for-reference-types.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3821.

```cpp
// C3821a.cpp
// compile with: /clr /c
public ref struct R {};
void test1(...) {
   R r;   // C3821
}
```

## <a name="example"></a>Příklad

Následující ukázka generuje C3821.

```cpp
// C3821b.cpp
// compile with: /clr
// processor: /x86
ref class A {
   public:
   int i;
};

int main() {
   // cannot use managed classes in this function
   A ^a;

   __asm {
      nop
   }
} // C3821
```
