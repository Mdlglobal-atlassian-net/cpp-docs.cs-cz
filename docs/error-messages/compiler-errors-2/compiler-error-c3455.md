---
title: Chyba kompilátoru C3455
ms.date: 11/04/2016
f1_keywords:
- C3455
helpviewer_keywords:
- C3455
ms.assetid: 218e5cfe-5391-4eeb-81c2-85c47e3a6cd2
ms.openlocfilehash: 4451ddbd8d5a7125112ef8e1c58e8843095bffd4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328573"
---
# <a name="compiler-error-c3455"></a>Chyba kompilátoru C3455

'attribute': žádný z konstruktů atributů argumentům neodpovídá

Chcete-li deklarovat atribut byla použita neplatná hodnota.  Zobrazit [atribut](../../windows/attributes/attribute.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C3455.

```
// C3455.cpp
// compile with: /clr /c
using namespace System;

[attribute("MyAt")]   // C3455
// try the following line instead
// [attribute(All)]
ref struct MyAttr {
   MyAttr() {}
};
```