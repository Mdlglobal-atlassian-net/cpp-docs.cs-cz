---
title: Upozornění (úroveň 1) C4806 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4806
dev_langs:
- C++
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b580500c3887fe60b7864280ad5ca1804752f2ae
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062602"
---
# <a name="compiler-warning-level-1-c4806"></a>Kompilátor upozornění (úroveň 1) C4806

'operation': nebezpečná operace: žádná hodnota typu 'type' povýšen na typ "typ" se nemůže rovnat dané konstantě

Tato zpráva zobrazí upozornění s kódem, jako `b == 3`, kde `b` má typ `bool`. Podpora pravidla Příčina `bool` má být převeden na `int`. Toto je právní, ale nemůže být nikdy **true**. Následující ukázka generuje C4806:

```
// C4806.cpp
// compile with: /W1
int main()
{
   bool b = true;
   // try..
   // int b = true;

   if (b == 3)   // C4806
   {
      b = false;
   }
}
```