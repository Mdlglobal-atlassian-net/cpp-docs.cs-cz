---
title: Upozornění kompilátoru (úroveň 4) C4516
ms.date: 11/04/2016
f1_keywords:
- C4516
helpviewer_keywords:
- C4516
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
ms.openlocfilehash: 47e278bbc69b972f6acc391d6b3278ab8d159c08
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990702"
---
# <a name="compiler-warning-level-4-c4516"></a>Upozornění kompilátoru (úroveň 4) C4516

' class:: symbol ': deklarace Access-Declarations jsou zastaralé; použití deklarace členů poskytuje lepší alternativu.

Výbor ANSI C++ deklaroval deklarace přístupu (Změna přístupu člena v odvozené třídě bez klíčového slova [using](../../cpp/using-declaration.md) ) na zastaralé. Deklarace přístupu nemusí být podporovány v budoucích verzích systému C++.

Následující ukázka generuje C4516:

```cpp
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
