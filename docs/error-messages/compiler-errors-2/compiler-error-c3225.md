---
title: Chyba kompilátoru C3225
ms.date: 11/04/2016
f1_keywords:
- C3225
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
ms.openlocfilehash: 1caa1e7ce787ffc14e615c946b5d670c75e0332a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757615"
---
# <a name="compiler-error-c3225"></a>Chyba kompilátoru C3225

Argument obecného typu pro ARG nemůže být typu Type, musí se jednat o typ hodnoty nebo typ popisovače.

Argument obecného typu není správného typu.

Další informace najdete v tématu [Obecné typy](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Nelze vytvořit instanci obecného typu s nativním typem. Následující ukázka generuje C3225.

```cpp
// C3225.cpp
// compile with: /clr
class A {};

ref class B {};

generic <class T>
ref class C {};

int main() {
   C<A>^ c = gcnew C<A>;   // C3225
   C<B^>^ c2 = gcnew C<B^>;   // OK
}
```

## <a name="example"></a>Příklad

Následující příklad vytvoří komponentu pomocí C#. Všimněte si, že omezení určuje, že obecný typ může být vytvořen pouze pomocí typu hodnoty.

```
// C3225_b.cs
// compile with: /target:library
// a C# program
public class MyList<T> where T: struct {}
```

## <a name="example"></a>Příklad

Tato ukázka využívá C#vytvořenou součást a porušuje omezení, že myList lze vytvořit pouze pomocí jiného typu hodnoty než <xref:System.Nullable>. Následující ukázka generuje C3225.

```cpp
// C3225_c.cpp
// compile with: /clr
#using "C3225_b.dll"
ref class A {};
value class B {};
int main() {
   MyList<A> x;   // C3225
   MyList<B> y;   // OK
}
```
