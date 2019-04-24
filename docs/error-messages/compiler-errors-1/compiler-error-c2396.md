---
title: Compiler Error C2396
ms.date: 11/04/2016
f1_keywords:
- C2396
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
ms.openlocfilehash: d320f78937fc60910bbed4a5b1b89841ea674fb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303512"
---
# <a name="compiler-error-c2396"></a>Compiler Error C2396

"your_type::operator'type": CLR nebo WinRT uživatelsky definovaný převod functionnot platný. Musíte převést nebo převést na: Nejde ^', 'T ^ %', 'T ^ & ", kde T ="your_type"

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