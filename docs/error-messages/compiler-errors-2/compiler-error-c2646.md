---
title: Chyba kompilátoru C2646
ms.date: 11/04/2016
f1_keywords:
- C2646
helpviewer_keywords:
- C2646
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
ms.openlocfilehash: a5c4dbc967c304fc6b13eb00e2c7093380ec8be9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758213"
---
# <a name="compiler-error-c2646"></a>Chyba kompilátoru C2646

anonymní struktura nebo sjednocení v globálním oboru názvů nebo oboru názvů musí být deklarované jako statické.

Anonymní struktura nebo sjednocení má globální obor názvů nebo obor názvů, ale není deklarována `static`.

Následující ukázka generuje C2646 a ukazuje, jak ji opravit:

```cpp
// C2646.cpp
// compile with: /c
union { int i; };   // C2646 not static

// OK
static union { int j; };
union U { int i; };
```
