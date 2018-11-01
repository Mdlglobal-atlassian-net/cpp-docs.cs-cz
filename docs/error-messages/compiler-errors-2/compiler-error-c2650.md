---
title: Chyba kompilátoru C2650
ms.date: 11/04/2016
f1_keywords:
- C2650
helpviewer_keywords:
- C2650
ms.assetid: 49a8ac6e-aa6d-4616-917c-a3cfcdbad5a4
ms.openlocfilehash: c7cbc12bff4e00613032a9d28b5be7533dce9612
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607997"
---
# <a name="compiler-error-c2650"></a>Chyba kompilátoru C2650

'operator': nemůže být virtuální funkce

A `new` nebo `delete` operátor deklarován `virtual`. Tyto operátory jsou `static` členské funkce a nemůže být `virtual`.

## <a name="example"></a>Příklad

Následující ukázka generuje C2650:

```
// C2650.cpp
// compile with: /c
class A {
   virtual void* operator new( unsigned int );   // C2650
   // try the following line instead
   // void* operator new( unsigned int );
};
```