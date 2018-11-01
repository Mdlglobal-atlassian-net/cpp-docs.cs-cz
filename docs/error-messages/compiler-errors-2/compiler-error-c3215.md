---
title: Chyba kompilátoru C3215
ms.date: 11/04/2016
f1_keywords:
- C3215
helpviewer_keywords:
- C3215
ms.assetid: d0d16007-8885-42e0-b086-2d3a61f348c5
ms.openlocfilehash: b9a6d9cd57572f65b24656fa527725c9c605143d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628264"
---
# <a name="compiler-error-c3215"></a>Chyba kompilátoru C3215

'type1': Parametr obecného typu už se omezuje podle 'type2'

Omezení byla zadána více než jednou.

Další informace o obecných typů viz [obecných typů](../../windows/generics-cpp-component-extensions.md).

Následující ukázka generuje C3215:

```
// C3215.cpp
// compile with: /clr
interface struct A {};

generic <class T>
where T : A,A
ref class C {};   // C3215
```

Možná řešení:

```
// C3215b.cpp
// compile with: /clr /c
interface struct A {};

generic <class T>
where T : A
ref class C {};
```