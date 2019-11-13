---
title: Upozornění kompilátoru (úroveň 1) C4788
ms.date: 11/04/2016
f1_keywords:
- C4788
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
ms.openlocfilehash: 03ce38aaa910a410025c5cccdf39646d34104779
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052391"
---
# <a name="compiler-warning-level-1-c4788"></a>Upozornění kompilátoru (úroveň 1) C4788

' identifier ': identifikátor byl zkrácen na ' Number ' znaků

Kompilátor omezuje maximální délku povolenou pro název funkce. Když kompilátor generuje funclets pro kód EH/SEH, vytvoří název funkce tím, že předčeká na název funkce nějaký text, například "__catch", "\__unwind" nebo jiný řetězec.

Výsledný název funkce může být příliš dlouhý a kompilátor ho zkrátí a vygeneruje C4788.

Chcete-li toto upozornění vyřešit, Zkraťte název původní funkce. Pokud je funkce C++ šablonou nebo metodou, použijte pro část názvu typedef. Příklad:

```cpp
C1<x, y, z<T>>::C2<a,b,c>::f
```

může nahradit:

```cpp
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;
new_class::f
```

Toto upozornění se objevuje pouze v kompilátoru x64.