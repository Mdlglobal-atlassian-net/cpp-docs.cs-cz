---
title: Chyba kompilátoru C2381
ms.date: 11/04/2016
f1_keywords:
- C2381
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
ms.openlocfilehash: 834b9939a99c694c702bb268b928575b4beb8856
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745392"
---
# <a name="compiler-error-c2381"></a>Chyba kompilátoru C2381

' function ': předefinování; __declspec (vrácení) se liší.

Funkce byla deklarována a pak definována, ale definice použila modifikátor `__declspec` [return](../../cpp/noreturn.md) . Použití `noreturn` představuje předefinování funkce; deklarace a definice musí souhlasit s používáním `noreturn`.

Následující ukázka generuje C2381:

```cpp
// C2381.cpp
// compile with: /c
void f1();
void __declspec(noreturn) f1() {}   // C2381
void __declspec(noreturn) f2() {}   // OK
```
