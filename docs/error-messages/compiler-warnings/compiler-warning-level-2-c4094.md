---
title: Upozornění kompilátoru (úroveň 2) C4094
ms.date: 11/04/2016
f1_keywords:
- C4094
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
ms.openlocfilehash: c90ad202e193f21955d396dd2aff6b39d3a968c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174333"
---
# <a name="compiler-warning-level-2-c4094"></a>Upozornění kompilátoru (úroveň 2) C4094

neznačkový token nedeklaruje žádné symboly.

Kompilátor zjistil prázdnou deklaraci pomocí netagované struktury, sjednocení nebo třídy. Deklarace se ignoruje.

## <a name="example"></a>Příklad

```cpp
// C4094.cpp
// compile with: /W2
struct
{
};   // C4094

int main()
{
}
```

Tato podmínka generuje chybu v rámci kompatibility ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).
