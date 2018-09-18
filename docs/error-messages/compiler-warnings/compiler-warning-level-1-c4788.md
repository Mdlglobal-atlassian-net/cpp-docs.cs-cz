---
title: Upozornění (úroveň 1) C4788 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4788
dev_langs:
- C++
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c8a6ad1aa3ae17944b8c2a292d484d55c24d9cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051721"
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