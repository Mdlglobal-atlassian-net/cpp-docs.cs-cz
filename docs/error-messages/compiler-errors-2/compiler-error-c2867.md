---
title: Chyba kompilátoru C2867 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2867
dev_langs:
- C++
helpviewer_keywords:
- C2867
ms.assetid: 63be26b2-d9ab-4f3d-a8b7-981ce3e4d6b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba16c619aa55636db7e52c03162446307bd8b62c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022250"
---
# <a name="compiler-error-c2867"></a>Chyba kompilátoru C2867

'identifier': není obor názvů

A `using` – direktiva se použije na něco jiného než obor názvů.

Následující ukázka generuje C2867:

```
// C2867.cpp
// compile with: /c
namespace N {
   class X {};
}
using namespace N::X;   // C2867
```