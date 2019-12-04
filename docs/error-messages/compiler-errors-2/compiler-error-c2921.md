---
title: Chyba kompilátoru C2921
ms.date: 11/04/2016
f1_keywords:
- C2921
helpviewer_keywords:
- C2921
ms.assetid: 323642a0-bfc4-4942-9f41-c3adf5c54296
ms.openlocfilehash: 82042b851282e686719ed54ccad0a2802afda22b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761016"
---
# <a name="compiler-error-c2921"></a>Chyba kompilátoru C2921

předefinování: Class: Šablona třídy nebo obecná se znovu deklaruje jako typ.

Obecná nebo šablona třídy obsahuje více deklarací, které nejsou ekvivalentní. Chcete-li tuto chybu opravit, použijte jiné názvy pro různé typy nebo odeberte předefinování názvu typu.

Následující ukázka generuje C2921:

```cpp
// C2921.cpp
// compile with: /c
template <class T> struct TC2 {};
typedef int TC2;   // C2921
// try the following line instead
// typedef struct TC2<int> x;   // OK - declare a template instance
```

K C2921 může také dojít při použití generických typů.

```cpp
// C2921b.cpp
// compile with: /clr /c
generic <class T> ref struct GC2 {};
typedef int GC2;   // C2921
// try the following line instead
// typedef ref struct GC2<int> x;
```
