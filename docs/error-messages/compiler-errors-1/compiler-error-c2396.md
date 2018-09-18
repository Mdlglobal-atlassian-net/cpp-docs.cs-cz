---
title: Chyba kompilátoru C2396 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2396
dev_langs:
- C++
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d69dfc1e296532f00ce9f44a178a366dca41e2e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061627"
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