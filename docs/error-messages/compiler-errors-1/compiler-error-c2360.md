---
title: Chyba kompilátoru C2360 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2360
dev_langs:
- C++
helpviewer_keywords:
- C2360
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f443c27c496d5d05c17bde854181b0fdde58f545
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089200"
---
# <a name="compiler-error-c2360"></a>Chyba kompilátoru C2360

Inicializace 'identifier' je podle popisku 'case' přeskočila.

Inicializace `identifier` mohly být přeskočeny, v `switch` příkazu. Nelze přejít po deklaraci s inicializátorem, není-li prohlášení je uzavřen v bloku. (Pokud je deklarovaná v rámci bloku, proměnná je v rámci oboru až do konce `switch` příkazu.)

Následující ukázka generuje C2360:

```
// C2360.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      int i = 1;
      { int j = 1; }
   case 1 :   // C2360
      int k = 1;
   }
}
```

Možná řešení:

```
// C2360b.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      { int j = 1; int i = 1;}
   case 1 :
      int k = 1;
   }
}
```