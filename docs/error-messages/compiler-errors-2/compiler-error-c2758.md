---
title: Chyba kompilátoru C2758
ms.date: 11/04/2016
f1_keywords:
- C2758
helpviewer_keywords:
- C2758
ms.assetid: 1d273034-194c-4926-9869-142d1b219cbe
ms.openlocfilehash: c854aeff1c57b8be6b445bc3615008519ca00af7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759513"
---
# <a name="compiler-error-c2758"></a>Chyba kompilátoru C2758

' member ': je nutné inicializovat člena typu odkazu.

Chyba kompilátoru C2758 je způsobena tím, že konstruktor neinicializuje člen odkazového typu v seznamu inicializátorů. Kompilátor opustí člena, který není definován. Proměnné člena reference musí být inicializovány při deklaraci nebo předány hodnotou v inicializačním seznamu konstruktoru.

Následující ukázka generuje C2758:

```cpp
// C2758.cpp
// Compile by using: cl /W3 /c C2758.cpp
struct A {
   const int i;

   A(int n) { };   // C2758
   // try the following line instead
   // A(int n) : i{n} {};
};
```
