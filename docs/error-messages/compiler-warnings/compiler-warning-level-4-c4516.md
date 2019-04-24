---
title: Kompilátor upozornění (úroveň 4) C4516
ms.date: 11/04/2016
f1_keywords:
- C4516
helpviewer_keywords:
- C4516
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
ms.openlocfilehash: 8020103e8e20bf1a5e955cbfdfafc6a328b439e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221030"
---
# <a name="compiler-warning-level-4-c4516"></a>Kompilátor upozornění (úroveň 4) C4516

'class::symbol': access-declarations jsou zastaralé; člen using-Declarations lepší alternativou

ANSI C++ výboru je deklarovaná deklarace přístupu (mění se přístup člena v odvozené třídě bez [pomocí](../../cpp/using-declaration.md) – klíčové slovo) zastaralé. Deklarace Access nemusí být podporována budoucí verze jazyka C++.

Následující ukázka generuje C4516:

```
// C4516.cpp
// compile with: /W4
class A
{
public:
   void x(char);
};

class B : protected A
{
public:
   A::x;  // C4516 on access-declaration
   // use the following line instead
   // using A::x; // using-declaration, ok
};

int main()
{
}
```