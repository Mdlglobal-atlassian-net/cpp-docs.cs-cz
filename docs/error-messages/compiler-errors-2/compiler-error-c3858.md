---
title: Chyba kompilátoru C3858
ms.date: 11/04/2016
f1_keywords:
- C3858
helpviewer_keywords:
- C3858
ms.assetid: 46e178d5-a55f-4ac6-a9dc-561fbcba5c1f
ms.openlocfilehash: e7fcc59ed6708cdf9d20db8d24e008f081e3eb6c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754794"
---
# <a name="compiler-error-c3858"></a>Chyba kompilátoru C3858

Typ: nejde znovu deklarovat v aktuálním oboru.

Typ nemůže být deklarovaný dvakrát ve stejném oboru.

Následující ukázka generuje C3858:

```cpp
// C3858.cpp
// compile with: /LD
template <class T>
struct Outer
{
   struct Inner;
};

template <class T>
struct Outer<T>::Inner;   // C3858
// try the following line instead
// struct Outer<T>::Inner{};
```
