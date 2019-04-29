---
title: Chyba kompilátoru C3799
ms.date: 11/04/2016
f1_keywords:
- C3799
helpviewer_keywords:
- C3799
ms.assetid: 336a2811-9370-4e6e-b03b-325bda470805
ms.openlocfilehash: 19ff414bde9bb24fca62fd10cfef6d18109199e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400120"
---
# <a name="compiler-error-c3799"></a>Chyba kompilátoru C3799

Indexovaná vlastnost nemůže mít prázdný seznam parametrů

Indexovaná vlastnost byl deklarován nesprávně. Další informace najdete v tématu [jak: Pomocí vlastností v C++vyhodnocovací](../../dotnet/how-to-use-properties-in-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3799 a ukazuje, jak ho opravit.

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