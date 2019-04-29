---
title: Chyba kompilátoru C3821
ms.date: 11/04/2016
f1_keywords:
- C3821
helpviewer_keywords:
- C3821
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
ms.openlocfilehash: 248431afb25aa4b9480818f76388f6ad56d8e006
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384228"
---
# <a name="compiler-error-c3821"></a>Chyba kompilátoru C3821

'function': spravovaný typ nebo funkci nelze použít v nespravované funkce

Funkcí s vloženým sestavením nebo [setjmp](../../c-runtime-library/reference/setjmp.md) nemůže obsahovat typy hodnot nebo spravované třídy. Chcete-li tuto chybu vyřešit, odeberte sestavení inline assemblerem a `setjmp` nebo odebrání spravovaných objektů.

C3821 může dojít, pokud se pokusíte použít automatického úložiště v funkce vararg.  Další informace najdete v tématu [seznamy argumentů proměnných (...) (C++Vyhodnocovací) ](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md) a [ C++ sémantika zásobníku pro odkazové typy](../../dotnet/cpp-stack-semantics-for-reference-types.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3821.

```
// C3821a.cpp
// compile with: /clr /c
public ref struct R {};
void test1(...) {
   R r;   // C3821
}
```

## <a name="example"></a>Příklad

Následující ukázka generuje C3821.

```
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
