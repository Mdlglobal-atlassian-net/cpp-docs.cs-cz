---
title: Chyba kompilátoru C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: 0150693ae84b45dc62c11cfdc59369eb25a819cd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757277"
---
# <a name="compiler-error-c3755"></a>Chyba kompilátoru C3755

Delegate: delegát se nedá definovat.

[Delegáta (C++ rozšíření komponent)](../../extensions/delegate-cpp-component-extensions.md) lze deklarovat, ale není definováno.

## <a name="example"></a>Příklad

Následující ukázka generuje C3755.

```cpp
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

## <a name="example"></a>Příklad

K C3755 může dojít také v případě, že se pokusíte vytvořit šablonu delegáta. Následující ukázka generuje C3755.

```cpp
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```
