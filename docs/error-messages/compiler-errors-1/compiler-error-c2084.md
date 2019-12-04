---
title: Chyba kompilátoru C2084
ms.date: 11/04/2016
f1_keywords:
- C2084
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
ms.openlocfilehash: 881ae051b2779fe674b31b64a7cbe7be7cf63705
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757888"
---
# <a name="compiler-error-c2084"></a>Chyba kompilátoru C2084

funkce Function*už má tělo.*

Funkce již byla definována.

Před Visual Studio 2002,

- Kompilátor by přijal více specializací šablony, které byly vyřešeny na stejný typ, i když další definice nebudou nikdy k dispozici. Kompilátor nyní detekuje tyto vícenásobné definice.

- `__int32` a `int` byly zpracovány jako samostatné typy. Kompilátor nyní zpracovává `__int32` jako synonymum pro `int`. To znamená, že kompilátor detekuje více definic, pokud je funkce přetížena v `__int32` i `int` a obsahuje chybu.

## <a name="example"></a>Příklad

Následující ukázka generuje C2084:

```cpp
// C2084.cpp
void Func(int);
void Func(int) {}   // define function
void Func(int) {}   // C2084 second definition
```

Tuto chybu opravíte tak, že odeberete duplicitní definici:

```cpp
// C2084b.cpp
// compile with: /c
void Func(int);
void Func(int) {}
```
