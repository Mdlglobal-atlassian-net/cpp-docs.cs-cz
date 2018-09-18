---
title: Chyba kompilátoru C3225 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3225
dev_langs:
- C++
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8d8b1251b9c13a71faf771c85924a75681deab7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033248"
---
# <a name="compiler-error-c3225"></a>Chyba kompilátoru C3225

argument obecného typu pro "argument" nemůže mít "typ", musí být typ hodnoty nebo typ popisovače

Argument obecného typu nebyl nesprávného typu.

Další informace najdete v tématu [obecných typů](../../windows/generics-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Nelze vytvořit instanci obecného typu pomocí nativního typu. Následující ukázka generuje C3225.

```
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

Následující příklad vytvoří komponentu pomocí jazyka C#. Všimněte si, že omezení určuje, že obecný typ může být vytvořena pouze s typem hodnoty.

```
// C3225_b.cs
// compile with: /target:library
// a C# program
public class MyList<T> where T: struct {}
```

## <a name="example"></a>Příklad

Tento příklad využívá jazyka C#-vytvořili komponentu a v rozporu s omezením, který může obsahovat jenom MyList vytvořena instance s typem hodnoty jiné než <xref:System.Nullable>. Následující ukázka generuje C3225.

```
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