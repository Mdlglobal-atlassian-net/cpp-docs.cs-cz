---
title: 'Postupy: pomocí výrazu gcnew vytváření typů hodnot s použitím implicitního zabalení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- gcnew keyword [C++], creating value types
- boxing, implicit
- value types, creating
ms.assetid: ceb48841-d6bd-47be-a167-57f44c961603
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b4d4a1a8a4531aa3de669acf48c4e37d556097a8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397838"
---
# <a name="how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing"></a>Postupy: Vytváření typů hodnot pomocí výrazu gcnew s použitím implicitního zabalení

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

## <a name="see-also"></a>Viz také

[Zabalení](../windows/boxing-cpp-component-extensions.md)