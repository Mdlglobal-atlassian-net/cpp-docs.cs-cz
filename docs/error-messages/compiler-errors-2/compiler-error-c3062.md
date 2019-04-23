---
title: Chyba kompilátoru C3062
ms.date: 11/04/2016
f1_keywords:
- C3062
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
ms.openlocfilehash: 6f4157db4a2a1b1864446a082deddc73df2e2fe9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778706"
---
# <a name="compiler-error-c3062"></a>Chyba kompilátoru C3062

"výčet": enumerátor vyžaduje hodnotu, protože základní typ je 'type'

Můžete určit nadřízený typ výčtu. Nicméně některé typy vyžadují, abyste přiřadit hodnoty pro každý čítač.

Další informace o výčtech naleznete v tématu [výčet tříd](../../extensions/enum-class-cpp-component-extensions.md).

Následující ukázka generuje C3062:

```
// C3062.cpp
// compile with: /clr

enum class MyEnum : bool { a };   // C3062
enum class MyEnum2 : bool { a = true};   // OK
```