---
title: Chyba kompilátoru C3740
ms.date: 11/04/2016
f1_keywords:
- C3740
helpviewer_keywords:
- C3740
ms.assetid: edb17a90-2307-4df6-943d-580460d26d2b
ms.openlocfilehash: dd493e4759b2fb70918bf94f14f4ada022e326b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547222"
---
# <a name="compiler-error-c3740"></a>Chyba kompilátoru C3740

šablony nelze zdroje ani je přijímat události

Třída šablony nebo struktura nemohou obsahovat [události](../../cpp/event-handling.md).

Následující ukázka generuje C3740:

```
// C3740.cpp
template <typename T>   // Delete the template specification
struct E {
   __event void f();   // C3740
};

int main() {
}
```