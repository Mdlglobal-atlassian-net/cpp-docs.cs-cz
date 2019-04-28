---
title: Chyba kompilátoru C2661
ms.date: 11/04/2016
f1_keywords:
- C2661
helpviewer_keywords:
- C2661
ms.assetid: 60021467-71cd-451b-9877-23840c69309f
ms.openlocfilehash: 14052fa3676396fe2ffc6ca86196025e7adab7d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360335"
---
# <a name="compiler-error-c2661"></a>Chyba kompilátoru C2661

'function': funkce overloaded má počet parametrů

Možné příčiny:

1. Nesprávný skutečných parametrů ve volání funkce.

1. Chybí deklarace funkce.

Následující ukázka generuje C2661:

```
// C2661.cpp
void func( int ){}
void func( int, int ){}
int main() {
   func( );   // C2661 func( void ) was not declared
   func( 1 );   // OK func( int ) was declared
}
```