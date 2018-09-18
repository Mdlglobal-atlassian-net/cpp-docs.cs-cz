---
title: Chyba kompilátoru C2909 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2909
dev_langs:
- C++
helpviewer_keywords:
- C2909
ms.assetid: 1c9df8ae-925d-4002-a5f8-a71413c45f9e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f611a026d0a969f49eaf2dcd93ba081bae052d10
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030882"
---
# <a name="compiler-error-c2909"></a>Chyba kompilátoru C2909

'identifier': explicitní vytváření instancí šablony funkcí vyžaduje návratový typ.

Explicitní vytváření instancí šablony funkcí vyžaduje, aby explicitní její typ vrácené hodnoty. Implicitní návratový typ specifikace nefunguje.

Následující ukázka generuje C2909:

```
// C2909.cpp
// compile with: /c
template<class T> int f(T);
template f<int>(int);         // C2909
template int f<int>(int);   // OK
```