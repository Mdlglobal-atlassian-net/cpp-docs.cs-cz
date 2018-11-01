---
title: Chyba kompilátoru C3222
ms.date: 11/04/2016
f1_keywords:
- C3222
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
ms.openlocfilehash: 9f2c245e98609c8da8f5f89902d5c51bbf9d2b4f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638669"
---
# <a name="compiler-error-c3222"></a>Chyba kompilátoru C3222

"parametr": nejdou deklarovat výchozí argumenty pro členské funkce spravované nebo WinRT typu nebo obecné funkce

Chcete-li deklarovat parametr metody s výchozí argument není povoleno. Formulář přetížené metody je jeden způsob, jak tento problém obejít. To znamená definovat metodu se stejným názvem se žádné parametry a potom inicializujte proměnnou v těle metody.

Následující ukázka generuje C3222:

```
// C3222_2.cpp
// compile with: /clr
public ref class G {
   void f( int n = 0 );   // C3222
};
```
