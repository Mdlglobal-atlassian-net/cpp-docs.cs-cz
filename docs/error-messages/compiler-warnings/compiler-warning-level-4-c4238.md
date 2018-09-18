---
title: Upozornění (úroveň 4) C4238 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4238
dev_langs:
- C++
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f4d5f358d08f81e6b8097140ad47d54f4b3b3fed
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057025"
---
# <a name="compiler-warning-level-4-c4238"></a>Kompilátor upozornění (úroveň 4) C4238

používá se nestandardní rozšíření: rvalue třídy se používá jako l-hodnoty.

Z důvodu kompatibility s předchozími verzemi sady Visual C++, rozšíření společnosti Microsoft (**/Ze**) vám umožní použít typ třídy jako r-hodnoty. v kontextu, který implicitně nebo explicitně přijímá jeho adresu. V některých případech, například v příkladu níže to může být nebezpečné.

## <a name="example"></a>Příklad

```
// C4238.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

C * pC = &C();   // C4238
```

Toto použití způsobí chybu podle kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).