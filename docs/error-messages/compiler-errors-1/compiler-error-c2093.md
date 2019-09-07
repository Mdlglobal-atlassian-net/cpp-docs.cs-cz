---
title: Chyba kompilátoru C2093
ms.date: 11/04/2016
f1_keywords:
- C2093
helpviewer_keywords:
- C2093
ms.assetid: 17529a70-9169-46b5-9fc6-57a5ce224e6a
ms.openlocfilehash: d57b452e63f7bf76051ef6a23c5f8f6ba81aed1e
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741144"
---
# <a name="compiler-error-c2093"></a>Chyba kompilátoru C2093

' variable1 ': nejde inicializovat pomocí adresy automatické proměnné ' rozsahu2 '.

Při kompilaci s [/za](../../build/reference/za-ze-disable-language-extensions.md)se program pokusil použít adresu automatické proměnné jako inicializátor.

Následující ukázka generuje C2093:

```
// C2093.c
// compile with: /Za /c
void func() {
   int li;   // an implicit auto variable
   int * s[]= { &li };   // C2093 address is not a constant

   // OK
   static int li2;
   int * s2[]= { &li2 };
}
```