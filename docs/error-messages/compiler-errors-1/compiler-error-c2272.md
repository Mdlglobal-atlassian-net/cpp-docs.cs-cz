---
title: Chyba kompilátoru C2272
ms.date: 11/04/2016
f1_keywords:
- C2272
helpviewer_keywords:
- C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
ms.openlocfilehash: fd6fdecd3a491ce5f068f4d51d413e6767aabe2f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758694"
---
# <a name="compiler-error-c2272"></a>Chyba kompilátoru C2272

' function ': Modifikátory nejsou povoleny pro statické členské funkce

Členská funkce `static` je deklarována s specifikátorem paměťového modelu, jako je například [const](../../cpp/const-cpp.md) nebo [volatile](../../cpp/volatile-cpp.md), a tyto modifikátory nejsou povoleny pro `static` členské funkce.

Následující ukázka generuje C2272:

```cpp
// C2272.cpp
// compile with: /c
class CMyClass {
public:
   static void func1() const volatile;   // C2272  func1 is static
   void func2() const volatile;   // OK
};
```
