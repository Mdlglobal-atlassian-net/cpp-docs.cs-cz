---
title: Chyba kompilátoru C2467
ms.date: 11/04/2016
f1_keywords:
- C2467
helpviewer_keywords:
- C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
ms.openlocfilehash: aa45cbb19519dea7bd5c8fb96abd2c76ea30a786
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302082"
---
# <a name="compiler-error-c2467"></a>Chyba kompilátoru C2467

Neplatná deklarace anonymního "uživatel definované type'

Vnořený typ definovaný uživatelem byl deklarován. Jedná se o chybu při kompilaci zdrojového kódu jazyka C s možností kompatibility standardu ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) povolena.

Následující ukázka generuje C2467:

```
//C2467.c
// compile with: /Za
int main() {
   struct X {
      union { int i; };   // C2467, nested declaration
   };
}
```