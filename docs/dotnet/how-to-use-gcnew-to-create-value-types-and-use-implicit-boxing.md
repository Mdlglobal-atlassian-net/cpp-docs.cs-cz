---
title: 'Postupy: Pomocí výrazu gcnew vytváření typů hodnot s použitím implicitního zabalení'
ms.date: 11/04/2016
helpviewer_keywords:
- gcnew keyword [C++], creating value types
- boxing, implicit
- value types, creating
ms.assetid: ceb48841-d6bd-47be-a167-57f44c961603
ms.openlocfilehash: 4b7d0560d8a80d0c09e7f8d0fce83748ec1f2f28
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739278"
---
# <a name="how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing"></a>Postupy: Pomocí výrazu gcnew vytváření typů hodnot s použitím implicitního zabalení

Pomocí [gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md) na hodnotě se vytvoří typ hodnotový typ, který pak může být umístěna na haldě spravované, uvolňování.

## <a name="example"></a>Příklad

```
// vcmcppv2_explicit_boxing4.cpp
// compile with: /clr
public value class V {
public:
   int m_i;
   V(int i) : m_i(i) {}
};

public ref struct TC {
   void do_test(V^ v) {
      if (v != nullptr)
         ;
      else
         ;
   }
};

int main() {
   V^ v = gcnew V(42);
   TC^ tc = gcnew TC;
   tc->do_test(v);
}
```

## <a name="see-also"></a>Viz také:

[Zabalení](../windows/boxing-cpp-component-extensions.md)
