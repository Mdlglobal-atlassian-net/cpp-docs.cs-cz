---
title: Chyba kompilátoru C2396
ms.date: 11/04/2016
f1_keywords:
- C2396
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
ms.openlocfilehash: 5020732ce5186ee1c6e9d2ea13f452fe9988bdfa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744833"
---
# <a name="compiler-error-c2396"></a>Chyba kompilátoru C2396

' your_type:: operator'type ' ': CLR nebo uživatelsky definovaný převod functionnot platný. Je nutné převést nebo převést na: t ^ ', n ^% ', ' ^ & ', kde T = ' your_type '.

Funkce převodu v prostředí Windows Runtime nebo spravovaném typu neobsahovala alespoň jeden parametr, jehož typ je stejný jako typ obsahující funkci převodu.

Následující ukázka generuje C2396 a ukazuje, jak ji opravit:

```cpp
// C2396.cpp
// compile with: /clr /c

ref struct Y {
   static operator int(char c);   // C2396

   // OK
   static operator int(Y^ hY);
   // or
   static operator Y^(char c);
};
```
