---
title: Chyba kompilátoru C2491
ms.date: 11/04/2016
f1_keywords:
- C2491
helpviewer_keywords:
- C2491
ms.assetid: 4e5a8f81-124e-402c-a5ec-d35a89b5469e
ms.openlocfilehash: 7ee7fb6e66ca9d5e09ad0eb445262c5f87d2060e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757069"
---
# <a name="compiler-error-c2491"></a>Chyba kompilátoru C2491

' identifier ': definice funkce dllimport není povolena

Data, statické datové členy a funkce mohou být deklarovány jako `dllimport`s, ale nejsou definovány jako `dllimport`s.

Chcete-li tento problém vyřešit, odeberte z definice funkce specifikátor `__declspec(dllimport)`.

Následující ukázka generuje C2491:

```cpp
// C2491.cpp
// compile with: /c
// function definition
void __declspec(dllimport) funcB() {}   // C2491

// function declaration
void __declspec(dllimport) funcB();   // OK
```
