---
title: Chyba kompilátoru C3831
ms.date: 11/04/2016
f1_keywords:
- C3831
helpviewer_keywords:
- C3831
ms.assetid: a125d8dc-b75a-4ea0-b6c7-fe7b119dba25
ms.openlocfilehash: 61ff2c7f7e99698ffbd521153663b1ab27bd6fde
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741596"
---
# <a name="compiler-error-c3831"></a>Chyba kompilátoru C3831

člen: Class nemůže mít připnutý datový člen nebo členskou funkci, která vrací ukazatel připnutí.

[pin_ptr (C++/CLI)](../../extensions/pin-ptr-cpp-cli.md) se nesprávně použil.

## <a name="example"></a>Příklad

Následující ukázka generuje C3831:

```cpp
// C3831a.cpp
// compile with: /clr
ref class Y
{
public:
   int i;
};

ref class X
{
   pin_ptr<int> mbr_Y;   // C3831
   int^ mbr_Y2;   // OK
};

int main() {
   Y y;
   pin_ptr<int> p = &y.i;
}
```
