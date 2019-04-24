---
title: Chyba kompilátoru C2753
ms.date: 11/04/2016
f1_keywords:
- C2753
helpviewer_keywords:
- C2753
ms.assetid: 92bfeeac-524a-4a8e-9a4f-fb8269055826
ms.openlocfilehash: e13c45cec99e60d8aec7dcc3db8e5a4813ea7de9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62228780"
---
# <a name="compiler-error-c2753"></a>Chyba kompilátoru C2753

"*šablony*': částečná specializace se nemůže shodovat seznam argumentů pro primární šablonu

Pokud seznam argumentů šablony odpovídá seznamu parametrů, kompilátor ho považuje za jednu šablonu. Definování stejné šablony dvakrát se nepovoluje.

## <a name="example"></a>Příklad

Následující ukázka generuje C2753 a ukazuje způsob, jak ho opravit:

```cpp
// C2753.cpp
// compile with: cl /c C2753.cpp
template<class T>
struct A {};

template<class T>
struct A<T> {};   // C2753
// try the following line instead
// struct A<int> {};

template<class T, class U, class V, class W, class X>
struct B {};
```