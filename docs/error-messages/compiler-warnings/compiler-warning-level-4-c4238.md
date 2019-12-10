---
title: Upozornění kompilátoru (úroveň 4) C4238
ms.date: 11/04/2016
f1_keywords:
- C4238
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
ms.openlocfilehash: cc913a4f92963437347fbc708eca03c25ab9d403
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991466"
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
