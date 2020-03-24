---
title: Upozornění kompilátoru (úroveň 1) C4667
ms.date: 11/04/2016
f1_keywords:
- C4667
helpviewer_keywords:
- C4667
ms.assetid: 5d2b7fe0-4f0e-4cd6-b432-ca02c3d194ab
ms.openlocfilehash: d306172dcc9904b2d0a32ce5fc6d85d35d6d74cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199430"
---
# <a name="compiler-warning-level-1-c4667"></a>Upozornění kompilátoru (úroveň 1) C4667

' function ': není definována žádná šablona funkcí, která by odpovídala vynucenému vytváření instancí

Nemůžete vytvořit instanci šablony funkce, která nebyla deklarována.

Následující ukázka způsobí C4667:

```cpp
// C4667a.cpp
// compile with: /LD /W1
template
void max(const int &, const int &); // C4667 expected
```

Chcete-li se tomuto upozornění vyhnout, nejprve deklarujte šablonu funkce:

```cpp
// C4667b.cpp
// compile with: /LD
// Declare the function template
template<typename T>
const T &max(const T &a, const T &b) {
   return (a > b) ? a : b;
}
// Then forcibly instantiate it with a desired type ... i.e. 'int'
//
template
const int &max(const int &, const int &);
```
