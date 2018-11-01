---
title: Kompilátor C4094 upozornění (úroveň 2)
ms.date: 11/04/2016
f1_keywords:
- C4094
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
ms.openlocfilehash: 73805afc897d14c6d2cc87490dfa0769a8de5193
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488397"
---
# <a name="compiler-warning-level-2-c4094"></a>Kompilátor C4094 upozornění (úroveň 2)

neoznačených "token" nedeklarovalo žádné symboly

Kompilátor zjistil deklaraci prázdný pomocí neoznačených struktury, sjednocení nebo třídy. Deklarace se ignoruje.

## <a name="example"></a>Příklad

```
// C4094.cpp
// compile with: /W2
struct
{
};   // C4094

int main()
{
}
```

Tato podmínka dojde k chybě v části kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).