---
title: Chyba linkerů LNK2020
ms.date: 11/04/2016
f1_keywords:
- LNK2020
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
ms.openlocfilehash: 9c6be2548e277af08f1069a70b26cd761db835bc
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988759"
---
# <a name="linker-tools-error-lnk2020"></a>Chyba linkerů LNK2020

Nerozpoznaný token ' token '

Podobně jako nedefinovaná externí chyba s tím rozdílem, že odkaz je prostřednictvím metadat. V metadatech musí být definovány všechny funkce a data.

Řešení je následující:

- Definujte chybějící funkci nebo data nebo

- Zahrňte soubor nebo knihovnu objektů, ve kterých je již definována chybějící funkce nebo data.

## <a name="example"></a>Příklad

Následující ukázka generuje LINKERŮ LNK2020.

```cpp
// LNK2020.cpp
// compile with: /clr /LD
ref struct A {
   A(int x);   // LNK2020
   static int f();   // LNK2020
};

// OK
ref struct B {
   B(int x) {}
   static int f() { return 0; }
};
```

## <a name="example"></a>Příklad

K LINKERŮ LNK2020 dojde také v případě, že vytvoříte proměnnou typu spravované šablony, ale nevytvoříte také instanci typu.

Následující ukázka generuje LINKERŮ LNK2020.

```cpp
// LNK2020_b.cpp
// compile with: /clr

template <typename T>
ref struct Base {
   virtual void f1() {};
};

template <typename T>
ref struct Base2 {
   virtual void f1() {};
};

int main() {
   Base<int>^ p;   // LNK2020
   Base2<int>^ p2 = gcnew Base2<int>();   // OK
};
```
