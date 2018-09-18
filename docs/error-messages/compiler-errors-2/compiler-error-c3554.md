---
title: Chyba kompilátoru C3554 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3554
dev_langs:
- C++
helpviewer_keywords:
- C3554
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b1760607a335d4dd56ec711eef76f5a68550d64
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089499"
---
# <a name="compiler-error-c3554"></a>Chyba kompilátoru C3554

"decltype" nelze kombinovat s jakékoli jiným specifikátorem typu.

Nelze zařadit `decltype()` – klíčové slovo pomocí jakékoli specifikátoru typu. Například následující fragment kódu vrátí chyba C3554.

```
int x;
unsigned decltype(x); // C3554
```