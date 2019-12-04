---
title: Chyba kompilátoru C2920
ms.date: 11/04/2016
f1_keywords:
- C2920
helpviewer_keywords:
- C2920
ms.assetid: 0a4cb2de-00a0-4209-8160-c7ce6ed7d9ab
ms.openlocfilehash: 2b744729097f7e697c7a7695a849b5ee46d7a4ab
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761029"
---
# <a name="compiler-error-c2920"></a>Chyba kompilátoru C2920

předefinování: Class: Šablona třídy nebo obecná už je deklarovaná jako typ.

Obecná nebo šablona třídy obsahuje více deklarací, které nejsou ekvivalentní. Chcete-li tuto chybu opravit, použijte jiné názvy pro různé typy nebo odeberte předefinování názvu typu.

Následující ukázka generuje C2920 a ukazuje, jak ji opravit:

```cpp
// C2920.cpp
// compile with: /c
typedef int TC1;
template <class T>
struct TC1 {};   // C2920
struct TC2 {};   // OK - fix by using a different name
```

C2920 může také nastat při použití generických typů:

```cpp
// C2920b.cpp
// compile with: /clr /c
typedef int GC1;
generic <class T>
ref struct GC1 {};   // C2920
ref struct GC2 {};   // OK - fix by using a different name
```
