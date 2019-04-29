---
title: Compiler Error C3196
ms.date: 11/04/2016
f1_keywords:
- C3196
helpviewer_keywords:
- C3196
ms.assetid: d9c38a13-191d-472d-aa2b-f61a6459d16c
ms.openlocfilehash: 252fef18fa98183dcc75219c1b802461f3bd2833
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402798"
---
# <a name="compiler-error-c3196"></a>Compiler Error C3196

! – klíčové slovo': používá více než jednou.

Klíčové slovo byl použit více než jednou.

Následující ukázka generuje C3196:

```
// C3196.cpp
// compile with: /clr
ref struct R abstract abstract {};   // C3196
ref struct S abstract {};   // OK
```