---
title: Chyba kompilátoru C3222 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3222
dev_langs:
- C++
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30231f74b379cd9d69806fbd4b49ba0cb55ad871
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048315"
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
