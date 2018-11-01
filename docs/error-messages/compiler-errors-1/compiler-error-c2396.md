---
title: Chyba kompilátoru C2396
ms.date: 11/04/2016
f1_keywords:
- C2396
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
ms.openlocfilehash: d320f78937fc60910bbed4a5b1b89841ea674fb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438086"
---
# <a name="compiler-error-c2396"></a>Chyba kompilátoru C2396

"your_type::operator'type'': CLR nebo WinRT functionnot uživatelsky definovaný převod platný. Musíte převést nebo převést na: t ^ ", nejde ^ %', 'T ^ &", kde T = "your_type"

Funkce převodu v prostředí Windows Runtime nebo spravovaný typ neměl nejmíň jeden parametr, jehož typ je stejný jako typ, který obsahuje funkce pro převod.

Následující ukázka generuje C2396 a ukazuje, jak ho opravit:

```
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