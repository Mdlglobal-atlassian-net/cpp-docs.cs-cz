---
title: Chyba kompilátoru C2362
ms.date: 11/04/2016
f1_keywords:
- C2362
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
ms.openlocfilehash: 17656b2a48a3680a9269d3ca300fd4188eda6b84
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364321"
---
# <a name="compiler-error-c2362"></a>Chyba kompilátoru C2362

Inicializace 'identifier' je přeskočených 'goto popisek.

Při kompilaci s [/Za](../../build/reference/za-ze-disable-language-extensions.md), přechod na popisek zabrání inicializaci identifikátor.

Nelze přejít po deklaraci s inicializátorem Pokud deklarace je uzavřen v bloku, který není zadán nebo již byl inicializován proměnné.

Následující ukázka generuje C2326:

```
// C2362.cpp
// compile with: /Za
int main() {
   goto label1;
   int i = 1;      // C2362, initialization skipped
label1:;
}
```

Možná řešení:

```
// C2362b.cpp
// compile with: /Za
int main() {
   goto label1;
   {
      int j = 1;   // OK, this block is never entered
   }
label1:;
}
```