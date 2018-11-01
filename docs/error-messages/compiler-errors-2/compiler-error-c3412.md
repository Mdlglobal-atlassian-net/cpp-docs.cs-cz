---
title: Chyba kompilátoru C3412
ms.date: 11/04/2016
f1_keywords:
- C3412
helpviewer_keywords:
- C3412
ms.assetid: aa4dd43b-54ce-4cda-85c1-1a77dd6e34fa
ms.openlocfilehash: 7c16ffa37f4d7192956afae26c825b63add1bfdd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540244"
---
# <a name="compiler-error-c3412"></a>Chyba kompilátoru C3412

"Šablona": nejde specializovat šablonu v aktuálním rozsahu.

V oboru třídy pouze v globální nebo obor názvů rozsahu nedá specializovat šablonu.

## <a name="example"></a>Příklad

Následující ukázka generuje C3412.

```
// C3412.cpp
template <class T>
struct S {
   template <>
   struct S<int> {};   // C3412 in a class
};
```

## <a name="example"></a>Příklad

Následující příklad ukazuje možným řešením.

```
// C3412b.cpp
// compile with: /c
template <class T>
struct S {};

template <>
struct S<int> {};
```