---
title: Chyba kompilátoru C2698 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2698
dev_langs:
- C++
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7ca3e7568640aabd2b7960d97ea94a11a1d5d59
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118918"
---
# <a name="compiler-error-c2698"></a>Chyba kompilátoru C2698

deklarace using pro ' Deklarace 1 nemůže koexistovat s existující deklarace using pro ' deklarace 2

Jakmile budete mít [using – deklarace](../../cpp/using-declaration.md) pro datového člena, jakékoli pomocí deklarace ve stejném oboru, který používá stejný název není povolená, protože mohou být přetíženy pouze funkce.

Následující ukázka generuje C2698:

```
// C2698.cpp
struct A {
   int x;
};

struct B {
   int x;
};

struct C : A, B {
   using A::x;
   using B::x;   // C2698
}
```