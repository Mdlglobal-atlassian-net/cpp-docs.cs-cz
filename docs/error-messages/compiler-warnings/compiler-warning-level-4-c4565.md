---
title: Kompilátor upozornění (úroveň 4) C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: b655dcfb456d32e45833e89e5a48926ad70d1d9e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588679"
---
# <a name="compiler-warning-level-4-c4565"></a>Kompilátor upozornění (úroveň 4) C4565

> "*funkce*': předefinování; symbol se předtím deklaroval s: __declspec (*modifikátor*)

## <a name="remarks"></a>Poznámky

Symbol se předefinovalo nebo došlo ke změně deklarace, a druhá definice nebo deklarace, na rozdíl od první definice nebo deklarace, neměl `__declspec` modifikátor (*modifikátor*). Toto upozornění je informační. Pokud chcete vyřešit toto upozornění, odstraňte jednu z definic.

## <a name="example"></a>Příklad

Následující ukázka generuje C4565:

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```