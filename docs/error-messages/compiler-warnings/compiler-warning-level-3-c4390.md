---
title: Upozornění kompilátoru (úroveň 3) C4390
ms.date: 11/04/2016
f1_keywords:
- C4390
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
ms.openlocfilehash: 8402c6a2d0fcbb4704b833ac7ae2b070c7af3a48
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051593"
---
# <a name="compiler-warning-level-3-c4390"></a>Upozornění kompilátoru (úroveň 3) C4390

; – našel se prázdný řízený příkaz; je tento záměr?

Za řídicím příkazem, který neobsahuje žádné instrukce, byl nalezen středník.

Pokud obdržíte C4390 z důvodu makra, měli byste použít direktivu pragma [Warning](../../preprocessor/warning.md) k zakázání C4390 v modulu, který obsahuje makro.

Následující ukázka generuje C4390:

```cpp
// C4390.cpp
// compile with: /W3
int main() {
   int i = 0;
   if (i);   // C4390
      i++;
}
```