---
title: Chyba kompilátoru C2355 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2355
dev_langs:
- C++
helpviewer_keywords:
- C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 456049c60ce39fce3cdbf04512f306027e30db25
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035185"
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