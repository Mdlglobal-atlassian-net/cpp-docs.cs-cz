---
title: Chyba kompilátoru C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: 5d1260138bfdbc318817c336077eef326b62f8b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386626"
---
# <a name="compiler-error-c3755"></a>Chyba kompilátoru C3755

'delegování': delegát nesmí být definovaná v

A [delegate (rozšíření komponent C++)](../../extensions/delegate-cpp-component-extensions.md) může být deklarovaná, ale není definovaný.

## <a name="example"></a>Příklad

Následující ukázka generuje C3755.

```
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

## <a name="example"></a>Příklad

C3755 může vzniknout také při pokusu o vytvoření šablony delegáta. Následující ukázka generuje C3755.

```
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```