---
title: Kompilátor upozornění (úroveň 4) C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: afb4fb493c7c3e34ca691720a30d74517b0ab5b7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661406"
---
# <a name="compiler-warning-level-4-c4559"></a>Kompilátor upozornění (úroveň 4) C4559

> "*funkce*': předefinování; zisky __declspec – funkce (*modifikátor*)

## <a name="remarks"></a>Poznámky

Funkce byla předefinovat nebo došlo ke změně deklarace, a druhá definice nebo deklarace přidána **__declspec** modifikátor (*modifikátor*). Toto upozornění je informační. Pokud chcete vyřešit toto upozornění, odstraňte jednu z definic.

## <a name="example"></a>Příklad

Následující ukázka generuje C4559:

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```