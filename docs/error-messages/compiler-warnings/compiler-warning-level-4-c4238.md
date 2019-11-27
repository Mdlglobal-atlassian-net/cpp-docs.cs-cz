---
title: Upozornění kompilátoru (úroveň 4) C4238
ms.date: 11/04/2016
f1_keywords:
- C4238
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
ms.openlocfilehash: 982457ded987f6aee4f2891bbb7d9103b830cc99
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541780"
---
# <a name="compiler-warning-level-4-c4238"></a>Upozornění kompilátoru (úroveň 4) C4238

používá se nestandardní rozšíření: rvalue třídy se používá jako lvalue.

Z důvodu kompatibility s předchozími verzemi C++vizuálů umožňuje rozšíření Microsoft Extensions ( **/ze**) použít typ třídy jako rvalue v kontextu, který implicitně nebo explicitně přebírá adresu. V některých případech, jako je například následující příklad, může být nebezpečné.

## <a name="example"></a>Příklad

```cpp
// C4238.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

C * pC = &C();   // C4238
```

Toto použití způsobuje chybu v rámci kompatibility ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).