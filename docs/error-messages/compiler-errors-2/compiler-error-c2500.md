---
title: Chyba kompilátoru C2500
ms.date: 11/04/2016
f1_keywords:
- C2500
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
ms.openlocfilehash: 152546fce8f3ee63f8b95595bff052f18cd4ebda
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746965"
---
# <a name="compiler-error-c2500"></a>Chyba kompilátoru C2500

' identifier1 ': ' identifier2 ' už je přímá základní (Base) třída

Třída nebo struktura se v seznamu základních tříd vyskytuje více než jednou.

Přímá základ je jedna uvedená v základním seznamu. Nepřímá základ je základní třídou jedné ze tříd v základním seznamu.

Třídu nelze zadat jako přímou základní třídu více než jednou. Třídu lze použít jako nepřímou základní třídu více než jednou.

Následující ukázka generuje C2500:

```cpp
// C2500.cpp
// compile with: /c
class A {};
class B : public A, public A {};    // C2500

// OK
class C : public A {};
class D : public A {};
class E : public C, public D {};
```
