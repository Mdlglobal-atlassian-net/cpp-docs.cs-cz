---
title: Chyba kompilátoru C2870
ms.date: 11/04/2016
f1_keywords:
- C2870
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
ms.openlocfilehash: f61281da23e46236e7fce496a4d89086e5d6c0ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165036"
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