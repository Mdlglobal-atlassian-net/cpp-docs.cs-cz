---
title: Závažná chyba C1016
ms.date: 11/04/2016
f1_keywords:
- C1016
helpviewer_keywords:
- C1016
ms.assetid: 33f45c3e-2d8f-43ad-a445-c412d1d54ce1
ms.openlocfilehash: b5774503297c596a351d72f3af4de6040628b078
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756952"
---
# <a name="fatal-error-c1016"></a>Závažná chyba C1016

\#ifdef očekával identifikátor # ifndef, který očekával identifikátor.

Direktiva podmíněné kompilace ([#ifdef](../../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md) nebo `#ifndef`) nemá žádný identifikátor k vyhodnocení. Chcete-li chybu vyřešit, zadejte identifikátor.

Následující ukázka generuje C1016:

```cpp
// C1016.cpp
#ifdef   // C1016
#define FC1016
#endif

int main() {}
```

Možné řešení:

```cpp
// C1016b.cpp
#ifdef X
#define FC1016
#endif

int main() {}
```
