---
title: Upozornění (úroveň 1) C4129 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4129
dev_langs:
- C++
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e02f38044180c45e221099d2874b7f8ff48d62f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098443"
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