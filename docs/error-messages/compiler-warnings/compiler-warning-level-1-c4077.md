---
title: Upozornění kompilátoru (úroveň 1) C4077
ms.date: 11/04/2016
f1_keywords:
- C4077
helpviewer_keywords:
- C4077
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
ms.openlocfilehash: fb9684b812e039bd37278f9f27db9225d0131f23
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626901"
---
# <a name="compiler-warning-level-1-c4077"></a>Upozornění kompilátoru (úroveň 1) C4077

Neznámá možnost check_stack

Původní forma direktivy pragma **check_stack** se používá s neznámým argumentem. Argument musí být `+`, `-`, `(on)`, `(off)`nebo prázdný.

Kompilátor ignoruje direktivu pragma a nechá kontrolu zásobníku beze změny.

## <a name="example"></a>Příklad

```cpp
// C4077.cpp
// compile with: /W1 /LD
#pragma check_stack yes // C4077
#pragma check_stack +    // Correct old form
#pragma check_stack (on) // Correct new form
```