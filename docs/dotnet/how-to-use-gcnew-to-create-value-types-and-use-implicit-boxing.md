---
title: 'Postupy: Pomocí výrazu gcnew vytváření typů hodnot s použitím implicitního zabalení'
ms.date: 11/04/2016
helpviewer_keywords:
- gcnew keyword [C++], creating value types
- boxing, implicit
- value types, creating
ms.assetid: ceb48841-d6bd-47be-a167-57f44c961603
ms.openlocfilehash: c67f8e0b9511f4ed1610e72e4a7df41c949b1d27
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58770794"
---
# <a name="how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing"></a>Postupy: Pomocí výrazu gcnew vytváření typů hodnot s použitím implicitního zabalení

Pomocí [gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md) na hodnotě se vytvoří typ hodnotový typ, který pak může být umístěna na haldě spravované, uvolňování.

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

[Zabalení](../extensions/boxing-cpp-component-extensions.md)
