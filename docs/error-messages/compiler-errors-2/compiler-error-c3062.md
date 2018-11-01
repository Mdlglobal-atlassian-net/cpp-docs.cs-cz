---
title: Chyba kompilátoru C3062
ms.date: 11/04/2016
f1_keywords:
- C3062
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
ms.openlocfilehash: ac45847c94e7d2dc731eba71b0a38105eb915e53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590408"
---
# <a name="compiler-error-c3062"></a>Chyba kompilátoru C3062

"výčet": enumerátor vyžaduje hodnotu, protože základní typ je 'type'

Můžete určit nadřízený typ výčtu. Nicméně některé typy vyžadují, abyste přiřadit hodnoty pro každý čítač.

Další informace o výčtech naleznete v tématu [výčet tříd](../../windows/enum-class-cpp-component-extensions.md).

Následující ukázka generuje C3062:

```
// C3062.cpp
// compile with: /clr

enum class MyEnum : bool { a };   // C3062
enum class MyEnum2 : bool { a = true};   // OK
```