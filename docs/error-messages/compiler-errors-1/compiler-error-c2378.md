---
title: Chyba kompilátoru C2378
ms.date: 11/04/2016
f1_keywords:
- C2378
helpviewer_keywords:
- C2378
ms.assetid: 507a91c6-ca72-48df-b3a4-2cf931c86806
ms.openlocfilehash: fb6d228826cf1b21904863505c0963069e89d32d
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344880"
---
# <a name="compiler-error-c2378"></a>Chyba kompilátoru C2378

'identifier': předefinování; symbol nemůže být přetížený s typedef

Tento identifikátor se předefinovalo jako `typedef`.

Následující ukázka generuje C2378:

```
// C2378.cpp
// compile with: /c
int i;
typedef int i;   // C2378
typedef int b;   // OK
```