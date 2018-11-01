---
title: Chyba kompilátoru C2500
ms.date: 11/04/2016
f1_keywords:
- C2500
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
ms.openlocfilehash: a5753fc99efcdb1064a21981c62faaba84d44189
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468364"
---
# <a name="compiler-error-c2500"></a>Chyba kompilátoru C2500

"identifier1": 'identifier2' je již přímé základní třídy.

Třída nebo struktura, zobrazí se více než jednou v seznamu základních tříd.

Přímou základní je uvedených v seznamu základních. Nepřímý základ je základní třídou jednoho v seznamu základních tříd.

Třídu nelze zadat více než jednou jako přímou základní třídu. Třída může sloužit jako nepřímou základní třídou více než jednou.

Následující ukázka generuje C2500:

```
// C2500.cpp
// compile with: /c
class A {};
class B : public A, public A {};    // C2500

// OK
class C : public A {};
class D : public A {};
class E : public C, public D {};
```