---
title: Upozornění (úroveň 1) C4326 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4326
dev_langs:
- C++
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cee18a9ccc807370cf2fb40748939f211a4ba52f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211001"
---
# <a name="compiler-warning-level-1-c4326"></a>Kompilátor upozornění (úroveň 1) C4326

> Návratový typ '*funkce*by měl být*type1*"namísto z"*type2*"

## <a name="remarks"></a>Poznámky

Funkce vrátí typu jiného než *type1*. Například použití [/Za](../../build/reference/za-ze-disable-language-extensions.md), **hlavní** nevrátil **int**.

## <a name="example"></a>Příklad

Následující ukázka generuje C4326 a ukazuje, jak ho opravit:

```cpp
// C4326.cpp
// compile with: /Za /W1
char main()
{
    // C4326, instead use int main()
}
```