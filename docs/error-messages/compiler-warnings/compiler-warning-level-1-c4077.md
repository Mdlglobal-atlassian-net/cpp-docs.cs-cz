---
title: Kompilátor upozornění (úroveň 1) C4077
ms.date: 11/04/2016
f1_keywords:
- C4077
helpviewer_keywords:
- C4077
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
ms.openlocfilehash: 5171ee79c3afd32e847483568fbbf90222747509
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208347"
---
# <a name="compiler-warning-level-1-c4077"></a>Kompilátor upozornění (úroveň 1) C4077

Neznámý parametr check_stack

Původní formě **check_stack –** – Direktiva pragma se používá se Neznámý argument. Argument musí být `+`, `-`, `(on)`, `(off)`, nebo je prázdný.

Kompilátor ignoruje direktivy pragma a ponechá beze změny kontroly zásobníku.

## <a name="example"></a>Příklad

```
// C4077.cpp
// compile with: /W1 /LD
#pragma check_stack yes // C4077
#pragma check_stack +    // Correct old form
#pragma check_stack (on) // Correct new form
```