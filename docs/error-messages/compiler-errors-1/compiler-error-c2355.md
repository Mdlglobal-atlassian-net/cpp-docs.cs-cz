---
title: Chyba kompilátoru C2355
ms.date: 11/04/2016
f1_keywords:
- C2355
helpviewer_keywords:
- C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
ms.openlocfilehash: 80871a73a7c3b4ad04b475539015f85d21ae88b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302641"
---
# <a name="compiler-error-c2355"></a>Chyba kompilátoru C2355

'this': může být odkazováno pouze uvnitř nestatické členské funkce nebo inicializátory členů nestatických dat

`this` Ukazatel je platný pouze v rámci nestatické členské funkce nebo inicializátory nestatických datových členů. K této chybě může dojít, pokud obor třídy definice členské funkce mimo deklaraci třídy není kvalifikován správně. K této chybě může dojít také při `this` ukazatel je použít ve funkci, která není deklarována ve třídě.

Chcete-li vyřešit tento problém, ujistěte se, že definice členské funkce odpovídá deklaraci členské funkce ve třídě, a že není deklarované jako statické. Pro inicializátory členů dat zkontrolujte, zda že datový člen není deklarované jako statické.

Následující ukázka generuje C2355 a ukazuje, jak ho opravit:

```
// C2355.cpp
// compile with: /c
class MyClass {};
MyClass *p = this;   // C2355

// OK
class MyClass2 {
public:
   void Test() {
      MyClass2 *p = this;
   }
};
```