---
title: Chyba kompilátoru C3141 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3141
dev_langs:
- C++
helpviewer_keywords:
- C3141
ms.assetid: b4fd65c3-50cc-46cd-8de0-6a6d24cb9cda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fda465b7cad2b46510b6f5e2dc4dc5d5fe82ecaf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038318"
---
# <a name="compiler-error-c3141"></a>Chyba kompilátoru C3141

'interface_name': rozhraní podporují jenom dědění typu public

Rozhraní, které jsou definovány [rozhraní (nebo __interface)](../../cpp/interface.md) – klíčové slovo podporují jenom dědění typu public.

Následující ukázka generuje C3141:

```
// C3141.cpp
__interface IBase {};
__interface IDerived1 : protected IBase {};  // C3141
__interface IDerived2 : private IBase {};    // C3141
```