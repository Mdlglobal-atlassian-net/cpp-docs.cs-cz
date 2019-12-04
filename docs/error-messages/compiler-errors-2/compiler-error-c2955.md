---
title: Chyba kompilátoru C2955
ms.date: 03/28/2017
f1_keywords:
- C2955
helpviewer_keywords:
- C2955
ms.assetid: 77709fb6-d69b-46fd-a62f-e8564563d01b
ms.openlocfilehash: 8afdeaf43c0c9789753b9165f1e8a8287aaac76d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742870"
---
# <a name="compiler-error-c2955"></a>Chyba kompilátoru C2955

' identifier ': použití šablony třídy nebo obecného aliasu vyžaduje šablonu nebo obecný seznam argumentů

Šablonu třídy nebo třídu Generic nemůžete použít jako identifikátor bez šablony nebo obecného seznamu argumentů.

Další informace naleznete v tématu [šablony tříd](../../cpp/class-templates.md).

Následující ukázka generuje C2955 a ukazuje, jak ji opravit:

```cpp
// C2955.cpp
// compile with: /c
template<class T>
class X {};

X x1;   // C2955
X<int> x2;   // OK - this is how to fix it.
```

K C2955 může také dojít při pokusu o provedení definice mimo řádek pro funkci deklarovanou v šabloně třídy:

```cpp
// C2955_b.cpp
// compile with: /c
template <class T>
class CT {
public:
   void CTFunc();
   void CTFunc2();
};

void CT::CTFunc() {}   // C2955

// OK - this is how to fix it
template <class T>
void CT<T>::CTFunc2() {}
```

C2955 může také nastat při použití generických typů:

```cpp
// C2955_c.cpp
// compile with: /clr
generic <class T>
ref struct GC {
   T t;
};

int main() {
   GC^ g;   // C2955
   GC <int>^ g;
}
```

## <a name="example"></a>Příklad

**Visual Studio 2017 a novější:** Kompilátor správně diagnostikuje chybějící seznamy argumentů šablony, když se šablona objeví v seznamu parametrů šablony (například jako součást výchozího argumentu šablony nebo Netypový parametr šablony). Následující kód je zkompilován v aplikaci Visual Studio 2015, ale vytváří chybu v aplikaci Visual Studio 2017.

```
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```
