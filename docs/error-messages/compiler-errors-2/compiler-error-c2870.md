---
title: Chyba kompilátoru C2870
ms.date: 11/04/2016
f1_keywords:
- C2870
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
ms.openlocfilehash: f61281da23e46236e7fce496a4d89086e5d6c0ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546366"
---
# <a name="compiler-error-c2870"></a>Chyba kompilátoru C2870

"name": definice oboru názvů musí být buď v rozsahu souboru, nebo v bezprostředně jiné definici oboru názvů

Definice oboru názvů `name` nesprávně. Obory názvů musí být definován v rozsahu souboru (mimo všechny bloky a třídy) nebo přímo v jiném oboru názvů.

Následující ukázka generuje C2870:

```
// C2870.cpp
// compile with: /c
int main() {
   namespace A { int i; };   // C2870
}
```