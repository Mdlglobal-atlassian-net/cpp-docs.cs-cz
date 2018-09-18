---
title: Chyba kompilátoru C2650 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2650
dev_langs:
- C++
helpviewer_keywords:
- C2650
ms.assetid: 49a8ac6e-aa6d-4616-917c-a3cfcdbad5a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37690727b76ec89ae9dffda2699e20e0a43f6938
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101043"
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