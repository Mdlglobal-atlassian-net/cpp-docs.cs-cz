---
title: Kompilátor upozornění (úroveň 1) C4788
ms.date: 11/04/2016
f1_keywords:
- C4788
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
ms.openlocfilehash: c51a4409c2a3028823462539343654b5eac365d0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187202"
---
# <a name="compiler-warning-level-1-c4788"></a>Kompilátor upozornění (úroveň 1) C4788

'identifier': identifikátor se zkrátil na znaků 'number'

Kompilátor omezuje maximální délku povolenou pro název funkce. Když kompilátor generuje funclets pro kód EH/SEH, tvoří název funkce předponou v podobě název funkce nějaký text, například "__catch", "\__unwind", nebo jiného řetězce.

Výsledný název funkce může být příliš dlouhý a bude ji zkrátit a generovat C4788 kompilátor.

Pokud chcete vyřešit toto upozornění, zkraťte název původní funkce. Pokud je funkce C++ šablony funkce nebo metoda, pomocí definice typu pro část názvu. Příklad:

```
C1<x, y, z<T>>::C2<a,b,c>::f
```

lze nahradit:

```
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;
new_class::f
```

Toto upozornění se zobrazí pouze v x64 kompilátoru.