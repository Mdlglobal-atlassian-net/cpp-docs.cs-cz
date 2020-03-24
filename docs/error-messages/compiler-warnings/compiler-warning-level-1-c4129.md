---
title: Upozornění kompilátoru (úroveň 1) C4129
ms.date: 11/04/2016
f1_keywords:
- C4129
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
ms.openlocfilehash: 1a48fc806f3274a59c99be25ac7a0e7b03a0454b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176218"
---
# <a name="compiler-warning-level-1-c4129"></a>Upozornění kompilátoru (úroveň 1) C4129

' Character ': Neznámá znaková řídicí sekvence

`character` za zpětným lomítkem (\\) ve znaku nebo v řetězcové konstantě není rozpoznána jako platná řídicí sekvence. Zpětné lomítko je ignorováno a není vytištěno. Znak následující po zpětném lomítku je vytištěn.

Chcete-li vytisknout jedno zpětné lomítko, zadejte dvojité zpětné lomítko (\\\\).

C++ Standard v části 2.13.2 popisuje sekvence escape.

Následující ukázka generuje C4129:

```cpp
// C4129.cpp
// compile with: /W1
int main() {
   char array1[] = "\/709";   // C4129
   char array2[] = "\n709";   // OK
}
```
