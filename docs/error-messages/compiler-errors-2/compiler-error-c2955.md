---
title: Chyba kompilátoru C2955
ms.date: 03/28/2017
f1_keywords:
- C2955
helpviewer_keywords:
- C2955
ms.assetid: 77709fb6-d69b-46fd-a62f-e8564563d01b
ms.openlocfilehash: c012e5189b9ca1d0b0e786cbddacedee7c6728d2
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519994"
---
# <a name="compiler-error-c2955"></a>Chyba kompilátoru C2955

'identifier': použít šablony třídy nebo alias obecný vyžaduje šablony nebo obecný seznam argumentů.

Šablony třídy nebo obecné třídy nelze použít jako identifikátor bez šablony nebo obecný seznam argumentů.

Další informace najdete v tématu [šablony třídy](../../cpp/class-templates.md).

Následující ukázka generuje C2955 a ukazuje, jak ho opravit:

```
// C2955.cpp
// compile with: /c
template<class T>
class X {};

X x1;   // C2955
X<int> x2;   // OK - this is how to fix it.
```

C2955 může dojít také při pokusu o definici mimo řádek pro funkce deklarované v šabloně třídy:

```
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

C2955 může dojít také při použití obecných typů:

```
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

**Visual Studio 2017 a novější:** kompilátor správně diagnostikuje chybějící seznamy argumentů šablony, když se šablona zobrazuje v seznamu parametrů šablony (například jako součást výchozí argument šablony nebo parametr šablony bez typu). Následující kód zkompiluje v sadě Visual Studio 2015, ale dojde k chybě v sadě Visual Studio 2017.

```
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```
