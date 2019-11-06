---
title: Upozornění kompilátoru (úroveň 1) C4103
ms.date: 11/04/2016
f1_keywords:
- C4103
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
ms.openlocfilehash: 456e7d393eb751e99c1969619ccfdcc649193c75
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627055"
---
# <a name="compiler-warning-level-1-c4103"></a>Upozornění kompilátoru (úroveň 1) C4103

filename: zarovnání se změnilo po zahrnutí hlavičky, může to být kvůli chybějícímu balíčku #pragma (pop).

Balení ovlivňuje rozložení tříd a běžně, pokud se změny rozbalí mezi soubory hlaviček, můžou nastat problémy.

Před ukončením hlavičkového souboru pro vyřešení tohoto upozornění použijte #pragma [Pack](../../preprocessor/pack.md)(pop).

Následující ukázka generuje C4103:

```cpp
// C4103.h
#pragma pack(push, 4)

// defintions and declarations

// uncomment the following line to resolve
// #pragma pack(pop)
```

A potom

```cpp
// C4103.cpp
// compile with: /LD /W1
#include "c4103.h"   // C4103
```