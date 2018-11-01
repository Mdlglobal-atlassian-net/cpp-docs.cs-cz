---
title: Upozornění kompilátoru (úroveň 2) C4099
ms.date: 11/04/2016
f1_keywords:
- C4099
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
ms.openlocfilehash: 09ea9e2963735c1e011e25b42b04ad6d67d084a5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471718"
---
# <a name="compiler-warning-level-2-c4099"></a>Upozornění kompilátoru (úroveň 2) C4099

'identifier': název typu se nejdřív zaznamenal s použitím objecttype1 nyní zaznamenal s použitím "objecttype2.

Objekt deklarovaný jako struktura je definována jako třída nebo objekt deklarovaný jako třída je definována jako struktury. Kompilátor používá typ zadaný v definici.

## <a name="example"></a>Příklad

Následující ukázka generuje C4099.

```
// C4099.cpp
// compile with: /W2 /c
struct A;
class A {};   // C4099, use different identifer or use same object type
```