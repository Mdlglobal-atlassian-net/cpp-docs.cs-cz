---
title: Chyba kompilátoru C2075 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2075
dev_langs:
- C++
helpviewer_keywords:
- C2075
ms.assetid: 8b1865d2-540b-4117-b982-e7a58a0b6cf7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ffedc5ce0ae073d53c32f6d0b9447987da31391a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083025"
---
# <a name="compiler-error-c2075"></a>Chyba kompilátoru C2075

'identifier': inicializace pole vyžaduje složených závorek

Nebyly žádné složených závorek kolem inicializátoru pro určené pole.

Následující ukázka generuje C2075:

```
// C2075.c
int main() {
   int i[] = 1, 2, 3 };   // C2075
}
```

Možná řešení:

```
// C2075b.c
int main() {
   int j[] = { 1, 2, 3 };
}
```