---
title: Compiler Error C2529
ms.date: 11/04/2016
f1_keywords:
- C2529
helpviewer_keywords:
- C2529
ms.assetid: 73a99e55-b91e-488d-9b72-cc80faaeb436
ms.openlocfilehash: b634f2369805114209860f5e304a7cd2cca2ec91
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266450"
---
# <a name="compiler-error-c2529"></a>Compiler Error C2529

"name": odkaz na odkaz je neplatný

Tuto chybu lze vyřešit pomocí syntaxe ukazatele a deklarační popisovač odkaz na ukazatel.

Následující ukázka generuje C2529:

```
// C2529.cpp
// compile with: /c
int i;
int &ri = i;
int &(&rri) = ri;   // C2529
```