---
title: Chyba kompilátoru C3174
ms.date: 11/04/2016
f1_keywords:
- C3174
helpviewer_keywords:
- C3174
ms.assetid: fe6b3b5a-8196-485f-a45f-0b2e51df4086
ms.openlocfilehash: 868d43e0796b7a6ab7398573e8b61efcb627d8a5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761722"
---
# <a name="compiler-error-c3174"></a>Chyba kompilátoru C3174

atribut Module není zadaný.

Program, který používá vizuální C++ atributy, nepoužívá také atribut [Module](../../windows/module-cpp.md) , který je vyžadován v jakémkoli programu, který používá atributy.

Následující ukázka generuje C3174:

```cpp
// C3174.cpp
// C3174 expected
// uncomment the following line to resolve this C3174
// [module(name="x")];
[export]
struct S
{
   int i;
};

int main()
{
}
```
