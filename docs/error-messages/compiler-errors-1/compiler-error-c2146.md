---
title: Compiler Error C2146
ms.date: 11/04/2016
f1_keywords:
- C2146
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
ms.openlocfilehash: f00de0ce491d517da11f251b89ccb9a7ae66b77d
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447264"
---
# <a name="compiler-error-c2146"></a>Compiler Error C2146

Chyba syntaxe: chybí token před identifikátor 'identifier'

Kompilátor očekává `token` a zjistili jsme `identifier` místo.  Možné příčiny:

1. Došlo k chybě pravopis a velká písmena.

1. Chybějící specifikátor typu v deklaraci identifikátoru.

Tato chyba může být způsobeno typografické chyby. Chyba [C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md) předchází obvykle k této chybě.

## <a name="example"></a>Příklad

Následující ukázka generuje C2146.

```
// C2146.cpp
class CDeclaredClass {};

class CMyClass {
   CUndeclared m_myClass;   // C2146
   CDeclaredClass m_myClass2;   // OK
};

int main() {
   int x;
   int t x;   // C2146 : missing semicolon before 'x'
}
```

## <a name="example"></a>Příklad

Tato chyba může být také generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual Studio .NET 2003: chybí `typename` – klíčové slovo.

Následující ukázka zkompiluje v sadě Visual Studio .NET 2002, ale selže v aplikaci Visual Studio .NET 2003:

```
// C2146b.cpp
// compile with: /c
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};

template <typename T>
X<T>::Y func() { }   // C2146

// OK
template <typename T>
typename X<T>::Y func() { }
```

## <a name="example"></a>Příklad

Zobrazí se také k této chybě v důsledku prací kompilátoru shoda pro Visual Studio .NET 2003: explicitní specializace již nelze najít parametry šablony z primární šablony.

Použití `T` z primární šablony není povolený v explicitní specializace. Pro kód je platný v aplikaci Visual Studio .NET 2003 a Visual Studio .NET nahraďte všechny výskyty parametr šablony ve specializaci typu explicitně specializovaný.

Následující ukázka zkompiluje v sadě Visual Studio .NET, ale selže v aplikaci Visual Studio .NET 2003:

```
// C2146_c.cpp
// compile with: /c
template <class T>
struct S;

template <>
struct S<int> {
   T m_t;   // C2146
   int m_t2;   // OK
};
```