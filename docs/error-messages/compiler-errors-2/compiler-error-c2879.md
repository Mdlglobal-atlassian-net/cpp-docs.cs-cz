---
title: Chyba kompilátoru C2879
ms.date: 11/04/2016
f1_keywords:
- C2879
helpviewer_keywords:
- C2879
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
ms.openlocfilehash: 9ac8f5e5edb1a6ed7314c5b5d125fcc9bfbe67de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677952"
---
# <a name="compiler-error-c2879"></a>Chyba kompilátoru C2879

'symbol': pouze existujícího oboru názvů může být dán alternativní název definice aliasu oboru názvů

Nelze vytvořit [aliasu oboru názvů](../../cpp/namespaces-cpp.md#namespace_aliases) symbol než obor názvů.

Následující ukázka generuje C2879:

```
// C2879.cpp
int main() {
   int i;
   namespace A = i;   // C2879 i is not a namespace
}
```