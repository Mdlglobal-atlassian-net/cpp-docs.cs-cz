---
title: Chyba kompilátoru C2034 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2034
dev_langs:
- C++
helpviewer_keywords:
- C2034
ms.assetid: 953d70fa-bde9-4ce6-a55d-741e7bc63ff4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b1dadc3249b7e58410eb153f8d298fca06a44ea7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034418"
---
# <a name="compiler-error-c2034"></a>Chyba kompilátoru C2034

'identifier': typ bitového pole je příliš malý počet bitů

Počet bitů v deklaraci bitového pole překračuje velikost základního typu.

Následující ukázka generuje C2034:

```
// C2034.cpp
struct A {
   char test : 9;   // C2034, char has 8 bits
};
```

Možná řešení:

```
// C2034b.cpp
// compile with: /c
struct A {
   char test : 8;
};
```