---
title: Chyba kompilátoru C3161 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3161
dev_langs:
- C++
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 11396ccad33489b41d18759ba4d2f00b445e94a3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136072"
---
# <a name="compiler-error-c3161"></a>Chyba kompilátoru C3161

'rozhraní': vnoření třídy, struktury, sjednocení nebo rozhraní v rozhraní je neplatný; vnoření rozhraní ve třídě, struktury nebo sjednocení je neplatný

[__Interface](../../cpp/interface.md) může být použit pouze v globálním oboru nebo v oboru názvů. Třída, struktura nebo sjednocení nemůže objevit v rozhraní.

## <a name="example"></a>Příklad

Následující ukázka generuje C3161.

```
// C3161.cpp
// compile with: /c
__interface X {
   __interface Y {};   // C3161 A nested interface
};
```