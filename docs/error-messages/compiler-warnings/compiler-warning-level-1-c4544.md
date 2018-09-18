---
title: Upozornění (úroveň 1) C4544 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4544
dev_langs:
- C++
helpviewer_keywords:
- C4544
ms.assetid: 11ee04df-41ae-435f-af44-881e801315a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c7cd274f0d1b595d374e1b108db40a51395b968
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084273"
---
# <a name="compiler-warning-level-1-c4544"></a>Kompilátor upozornění (úroveň 1) C4544

"deklarace": výchozí argument šablony pro tuto deklaraci šablony ignoruje.

Výchozí argument šablony byla zadána nesprávná místě a byla ignorována. Výchozí argument šablony pro šablonu tříd můžete zadat jenom v deklaraci nebo definici šablony třídy a ne na člena šablony třídy.

Tato ukázka vygeneruje C4545 a další příklad ukazuje, jak ho opravit:

```
// C4544.cpp
// compile with: /W1 /LD
template <class T>
struct S
{
   template <class T1>
      struct S1;
   void f();
};

template <class T=int>
template <class T1>
struct S<T>::S1 {};   // C4544
```

V tomto příkladu výchozího parametru se vztahuje na šablonu třídy `S`:

```
// C4544b.cpp
// compile with: /LD
template <class T = int>
struct S
{
   template <class T1>
      struct S1;
   void f();
};

template <class T>
template <class T1>
struct S<T>::S1 {};
```