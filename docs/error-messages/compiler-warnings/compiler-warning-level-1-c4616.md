---
title: Kompilátor upozornění (úroveň 1) C4616
ms.date: 11/04/2016
f1_keywords:
- C4616
helpviewer_keywords:
- C4616
ms.assetid: 71e15265-c5bc-42ce-a6a9-4879892472b1
ms.openlocfilehash: d63e1abffce617a48ac1a5cd8c61feba941b31ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599087"
---
# <a name="compiler-warning-level-1-c4616"></a>Kompilátor upozornění (úroveň 1) C4616

\#– Direktiva pragma upozornění: číslo upozornění 'number' není platné upozornění kompilátoru

Číslo upozornění podle [upozornění](../../preprocessor/warning.md) – Direktiva pragma nelze přiřadit. Direktivy pragma se ignoruje.

Následující ukázka generuje C4616:

```
// C4616.cpp
// compile with: /W1 /c
#pragma warning( disable : 0 )   // C4616
#pragma warning( disable : 999 )   // OK
#pragma warning( disable : 4998 )   // OK
```