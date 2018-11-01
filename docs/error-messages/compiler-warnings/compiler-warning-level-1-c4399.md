---
title: Kompilátor upozornění (úroveň 1) C4399
ms.date: 11/04/2016
f1_keywords:
- C4399
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
ms.openlocfilehash: 56fe0f314142d873fc02136bc2c3fe65e71f4dda
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544063"
---
# <a name="compiler-warning-level-1-c4399"></a>Kompilátor upozornění (úroveň 1) C4399

> "*symbol*': symbol na úrovni jednotlivého procesu nesmí být označené __declspec(dllimport) při kompilaci s parametrem/CLR: pure

## <a name="remarks"></a>Poznámky

**/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Nelze importovat data z nativní bitové kopie nebo bitové nativní a konstrukce CLR do čistého image. Pokud chcete vyřešit toto upozornění, proveďte kompilaci s **/CLR** (není **/CLR: pure**) nebo odstranění `__declspec(dllimport)`.

## <a name="example"></a>Příklad

Následující ukázka generuje C4399.

```cpp
// C4399.cpp
// compile with: /clr:pure /doc /W1 /c
__declspec(dllimport) __declspec(process) extern const int i;   // C4399
```