---
title: Chyba kompilátoru C2243
ms.date: 11/04/2016
f1_keywords:
- C2243
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
ms.openlocfilehash: f5a62b1c12b94735d0383697bf7a92d12d64b21f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757797"
---
# <a name="compiler-error-c2243"></a>Chyba kompilátoru C2243

typ převodu ' conversion ' na ' typ2 ' existuje, ale je nepřístupný

Aplikace Access Protection (`protected` nebo `private`) zabránila převodu z ukazatele na odvozenou třídu na ukazatel na základní třídu.

Následující ukázka generuje C2243:

```cpp
// C2243.cpp
// compile with: /c
class B {};
class D : private B {};
class E : public B {};

D d;
B *p = &d;   // C2243

E e;
B *p2 = &e;
```

Základní třídy s `protected` nebo `private` přístup nejsou k dispozici pro klienty odvozené třídy. Tyto úrovně řízení přístupu označují, že základní třída je podrobností implementace, které by měly být pro klienty neviditelné. Použijte veřejné odvození, pokud chcete, aby klienti odvozené třídy měli přístup k implicitnímu převodu ukazatele odvozené třídy na ukazatel na základní třídu.
