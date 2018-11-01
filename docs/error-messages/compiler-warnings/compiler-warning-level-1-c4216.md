---
title: Kompilátor upozornění (úroveň 1) C4216
ms.date: 11/04/2016
f1_keywords:
- C4216
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
ms.openlocfilehash: 43c72855dbb40e93cb219e4461dbbf81d086ea79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650915"
---
# <a name="compiler-warning-level-1-c4216"></a>Kompilátor upozornění (úroveň 1) C4216

používá se nestandardní rozšíření: float long

Výchozí rozšíření společnosti Microsoft (/Ze) považovat **float long** jako **double**. Kompatibilita s ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) nepodporuje. Použití **double** zachovala kompatibilita. Následující ukázka generuje C4216:

```
// C4216.cpp
// compile with: /W1
float long a;   // C4216

// use the line below to resolve the warning
// double a;

int main() {
}
```