---
title: Chyba kompilátoru C3454
ms.date: 11/04/2016
f1_keywords:
- C3454
helpviewer_keywords:
- C3454
ms.assetid: dc4e6d57-5b4d-4114-8d6f-22f9ae62925b
ms.openlocfilehash: 1909dc772413c16d39271dc839a0ec0db206da03
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756679"
---
# <a name="compiler-error-c3454"></a>Chyba kompilátoru C3454

[Attribute] není povolený pro deklaraci třídy.

Třída musí být definována, aby mohla být atributem.

Další informace naleznete v tématu [attribute](../../windows/attributes/attribute.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3454.

```cpp
// C3454.cpp
// compile with: /clr /c
using namespace System;

[attribute]   // C3454
ref class Attr1;

[attribute]   // OK
ref class Attr2 {};
```
