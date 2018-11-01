---
title: Chyba kompilátoru C2272
ms.date: 11/04/2016
f1_keywords:
- C2272
helpviewer_keywords:
- C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
ms.openlocfilehash: 1a5a1e47a721cb6edd795012cc45943e63708936
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537420"
---
# <a name="compiler-error-c2272"></a>Chyba kompilátoru C2272

'function': Modifikátory není povolený u statických členských funkcí

A `static` členská funkce je deklarována s specifikátorem paměťový model, jako například [const](../../cpp/const-cpp.md) nebo [volatile](../../cpp/volatile-cpp.md), a tyto modifikátory nejsou povolené u `static` členské funkce.

Následující ukázka generuje C2272:

```
// C2272.cpp
// compile with: /c
class CMyClass {
public:
   static void func1() const volatile;   // C2272  func1 is static
   void func2() const volatile;   // OK
};
```