---
title: Kompilátor upozornění (úroveň 1) C4129
ms.date: 11/04/2016
f1_keywords:
- C4129
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
ms.openlocfilehash: dc4f4c4c1feeba543ce0baa71e1ee5dfd81fdcae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428665"
---
# <a name="compiler-warning-level-1-c4129"></a>Kompilátor upozornění (úroveň 1) C4129

'znak': nerozpoznaný znak řídicí sekvence

`character` Následující zpětné lomítko (\\) v znak nebo řetězec – konstanta nebyl rozpoznán jako platný řídicí sekvence. Zpětné lomítko je ignorována, ne k tisku. Znak po zpětném lomítku je vytištěna.

Chcete-li vytisknout jedno zpětné lomítko, zadejte dvojité zpětné lomítko (\\\\).

Standard jazyka C++ v části 2.13.2 popisuje řídicí sekvence.

Následující ukázka generuje C4129:

```
// C4129.cpp
// compile with: /W1
int main() {
   char array1[] = "\/709";   // C4129
   char array2[] = "\n709";   // OK
}
```