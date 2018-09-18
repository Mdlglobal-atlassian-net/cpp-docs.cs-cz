---
title: Chyba kompilátoru C3062 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3062
dev_langs:
- C++
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95f2e58cada0b1b825fb0f065b461db6350de9fc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067165"
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