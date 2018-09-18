---
title: Chyba kompilátoru C2283 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2283
dev_langs:
- C++
helpviewer_keywords:
- C2283
ms.assetid: 8a5b3175-b480-4598-a1f7-0b50504c5caa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c90c355a1c2ecd19ccd7b2fc25e75f53d4f9414
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070116"
---
# <a name="compiler-error-c2283"></a>Chyba kompilátoru C2283

'identifier': specifikátor pure nebo abstract override není povolený pro nepojmenované struktury

Členská funkce Nepojmenovaná třída nebo struktura je deklarována s specifikátor pure, což není povoleno.

Následující ukázka generuje C2283:

```
// C2283.cpp
// compile with: /c
struct {
   virtual void func() = 0;   // C2283
};
struct T {
   virtual void func() = 0;   // OK
};
```