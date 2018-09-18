---
title: Upozornění (úroveň 1) C4618 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4618
dev_langs:
- C++
helpviewer_keywords:
- C4618
ms.assetid: 6ff10d0a-6d5b-4373-8196-1d57bb6b1611
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ff6080d6315156a1dbaeb89fae1d5cb10865405
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074263"
---
# <a name="compiler-warning-level-1-c4618"></a>Kompilátor upozornění (úroveň 1) C4618

v parametrech direktivy pragma zahrnuté prázdný řetězec; pragma se ignoruje

Řetězec s hodnotou null byl zadán jako argument **#pragma**.

Direktivy pragma byl zpracován bez argumentu.

Následující ukázka generuje C4618:

```
// C4618.cpp
// compile with: /W1 /LD
#pragma code_seg("")   // C4618
```