---
title: Upozornění kompilátoru (úroveň 4) C4019
ms.date: 11/04/2016
f1_keywords:
- C4019
helpviewer_keywords:
- C4019
ms.assetid: 4ecfe85d-673f-4334-8154-36fe7f0b3444
ms.openlocfilehash: b15d024f217280fb4fc49242f4bfc1e7fcc2b303
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541228"
---
# <a name="compiler-warning-level-4-c4019"></a>Upozornění kompilátoru (úroveň 4) C4019

prázdný příkaz v globálním oboru

Středníkem v globálním oboru nepředchází příkaz.

Toto upozornění může být opraveno při odebrání nadbytečného středníku.

## <a name="example"></a>Příklad

```c
// C4019.c
// compile with: /Za /W4
#define declint( varname ) int varname;
declint( a );   // C4019, int a;;
declint( b )   // OK, int b;

int main()
{
}
```