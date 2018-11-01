---
title: Chyba kompilátoru C2199
ms.date: 11/04/2016
f1_keywords:
- C2199
helpviewer_keywords:
- C2199
ms.assetid: 6a92a1b7-7906-49e6-a31f-e8bffbc7706a
ms.openlocfilehash: e5892a537cbf337b23ff2356583cec4bf5925677
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530968"
---
# <a name="compiler-error-c2199"></a>Chyba kompilátoru C2199

Chyba syntaxe: nenašel se identifikátor ("v globálním oboru (byla deklarace úmyslná?)

Zadaný kontext způsobila chybu syntaxe. Může být nesprávná deklarace syntaxe.

Následující ukázka generuje C2199:

```
// C2199.cpp
// compile with: /c
int j = int(1) int(1);   // C2199
int j = 1;   // OK
```