---
title: Chyba kompilátoru C3799
ms.date: 11/04/2016
f1_keywords:
- C3799
helpviewer_keywords:
- C3799
ms.assetid: 336a2811-9370-4e6e-b03b-325bda470805
ms.openlocfilehash: 980683ebc2e086e4c16180f04466af9dbdd49d02
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165649"
---
# <a name="compiler-error-c3799"></a>Chyba kompilátoru C3799

indexovaná vlastnost nemůže mít prázdný seznam parametrů.

Indexovaná vlastnost byla deklarována nesprávně. Další informace najdete v tématu [Postupy: použití vlastností C++v/CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3799 a ukazuje, jak ji opravit.

```cpp
// C3799.cpp
// compile with: /clr /c
ref struct C {
   property int default[] {   // C3799
   // try the following line instead
   // property int default[int] {
      int get(int index) { return 0; }
      void set(int index, int value) {}
   }
};
```
