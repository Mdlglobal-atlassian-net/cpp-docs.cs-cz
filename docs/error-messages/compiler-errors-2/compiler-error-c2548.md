---
title: Chyba kompilátoru C2548
ms.date: 11/04/2016
f1_keywords:
- C2548
helpviewer_keywords:
- C2548
ms.assetid: 01e9c835-9bf3-4020-9295-5ee448c519f3
ms.openlocfilehash: 2c680d86a0ea69d67f9e53a481f2f096f4cc7878
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659584"
---
# <a name="compiler-error-c2548"></a>Chyba kompilátoru C2548

'class::member': Chybí výchozí parametr parametru parametr

Výchozí seznam parametrů chybí parametr. Pokud zadáte parametr výchozí kdekoli v seznamu parametrů, je nutné definovat výchozí parametry pro všechny následující parametry.

## <a name="example"></a>Příklad

Následující ukázka generuje C2548:

```
// C2548.cpp
// compile with: /c
void func( int = 1, int, int = 3);  // C2548

// OK
void func2( int, int, int = 3);
void func3( int, int = 2, int = 3);
```