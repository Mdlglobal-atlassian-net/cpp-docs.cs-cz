---
title: Upozornění kompilátoru (úroveň 1) C4129
ms.date: 11/04/2016
f1_keywords:
- C4129
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
ms.openlocfilehash: ab3108c60c18276e8e4797c7cfde1b66535dbaaa
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627425"
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