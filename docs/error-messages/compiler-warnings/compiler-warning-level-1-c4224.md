---
title: Upozornění kompilátoru (úroveň 1) C4224
ms.date: 11/04/2016
f1_keywords:
- C4224
helpviewer_keywords:
- C4224
ms.assetid: 1531cae0-5040-49fd-b149-005bb5085391
ms.openlocfilehash: e2e6cde3cc3c6d3032bfbf4e81959ae791a91981
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199781"
---
# <a name="compiler-warning-level-1-c4224"></a>Upozornění kompilátoru (úroveň 1) C4224

používá se nestandardní rozšíření: formální parametr Identifier byl dřív definovaný jako typ.

Identifikátor byl dříve použit jako `typedef`. To způsobí upozornění v případě kompatibility ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="example"></a>Příklad

```cpp
// C4224.cpp
// compile with: /Za /W1 /LD
typedef int I;
void func ( int I );  // C4224
```
