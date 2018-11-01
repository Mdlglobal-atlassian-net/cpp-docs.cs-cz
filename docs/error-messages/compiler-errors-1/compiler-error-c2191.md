---
title: Chyba kompilátoru C2191
ms.date: 11/04/2016
f1_keywords:
- C2191
helpviewer_keywords:
- C2191
ms.assetid: 051b8350-e5de-4f51-ab6e-96d32366bcef
ms.openlocfilehash: 23dfe1d95ab75f253fc2a7b4b00dfcd1aaaa3bbf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623519"
---
# <a name="compiler-error-c2191"></a>Chyba kompilátoru C2191

druhý seznam parametrů je delší než první.

Funkce jazyka C se deklaroval podruhé s delší seznam parametrů. C nepodporuje přetížené funkce.

## <a name="example"></a>Příklad

Následující ukázka generuje C2191:

```
// C2191.c
// compile with: /Za /c
void func( int );
void func( int, float );   // C2191 different parameter list
void func2( int, float );   // OK
```