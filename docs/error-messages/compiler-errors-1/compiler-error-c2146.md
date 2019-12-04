---
title: Chyba kompilátoru C2146
ms.date: 11/04/2016
f1_keywords:
- C2146
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
ms.openlocfilehash: 8dc7b521243c4eafdc22fab851812b6c12b004cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755912"
---
# <a name="compiler-error-c2146"></a>Chyba kompilátoru C2146

Chyba syntaxe: před identifikátorem Identifier chybí token.

Kompilátor očekával `token` a místo toho se našel `identifier`.  Možné příčiny:

1. Chyba pravopisu nebo psaní velkých písmen.

1. V deklaraci identifikátoru chybí specifikátor typu.

Tato chyba může být způsobena typografickou chybou. Chyba [C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md) obvykle předchází této chybě.

## <a name="example"></a>Příklad

Následující ukázka generuje C2146.

```cpp
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

Tato chyba se může vygenerovat taky v důsledku práce s shodami s kompilátorem, která se dokončila pro Visual Studio .NET 2003: chybí klíčové slovo `typename`.

Následující ukázka kompiluje v aplikaci Visual Studio .NET 2002, ale v aplikaci Visual Studio .NET 2003 se nezdaří:

```cpp
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

Tato chyba se zobrazí také v důsledku práce s vyhovujícími kompilátory, které byly provedeny pro sadu Visual Studio .NET 2003: explicitní specializace již nenaleznou parametry šablony z primární šablony.

Použití `T` z primární šablony není v explicitní specializaci povoleno. Pro kód, který bude platný v prostředí Visual Studio .NET 2003 a Visual Studio .NET, nahraďte všechny výskyty parametru Template v specializaci explicitním specializovaném typem.

Následující ukázka kompiluje v aplikaci Visual Studio .NET, ale v aplikaci Visual Studio .NET 2003 se nezdaří:

```cpp
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
