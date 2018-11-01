---
title: Chyba kompilátoru C3168
ms.date: 11/04/2016
f1_keywords:
- C3168
helpviewer_keywords:
- C3168
ms.assetid: 4c36fcfb-c351-48ff-b4eb-78d2aa1b4d55
ms.openlocfilehash: f39160cc09825c6d87d56ff5ba80d21a35f41e12
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676561"
---
# <a name="compiler-error-c3168"></a>Chyba kompilátoru C3168

'type': Neplatný podkladový typ pro výčet

Podkladový typ zadaný pro `enum` typu nebyl platný. Základní typ musí být celočíselného typu jazyka C++ nebo odpovídající typ CLR.

Následující ukázka generuje C3168:

```
// C3168.cpp
// compile with: /clr /c
ref class G{};

enum class E : G { e };   // C3168
enum class F { f };   // OK
```
