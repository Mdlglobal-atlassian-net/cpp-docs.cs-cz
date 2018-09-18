---
title: Chyba kompilátoru C2042 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2042
dev_langs:
- C++
helpviewer_keywords:
- C2042
ms.assetid: e111788f-41ce-405a-9824-a4c1c26059e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cbc1d0d5ec0781ebf203a2cebcd99a58996c6547
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079996"
---
# <a name="compiler-error-c2042"></a>Chyba kompilátoru C2042

podepsané nebo nepodepsané klíčová slova vzájemně se vylučuje

Klíčová slova `signed` a `unsigned` se používají v jedné deklaraci.

Následující ukázka generuje C2042:

```
// C2042.cpp
unsigned signed int i;   // C2042
```

Možná řešení:

```
// C2042b.cpp
// compile with: /c
unsigned int i;
signed int ii;
```