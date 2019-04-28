---
title: Chyba kompilátoru C2010
ms.date: 11/04/2016
f1_keywords:
- C2010
helpviewer_keywords:
- C2010
ms.assetid: 5795ed1d-e206-410b-b7b4-528d125c67b4
ms.openlocfilehash: 71cb0012f5e7bda3a0f1409fe71649a5bd0944b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362033"
---
# <a name="compiler-error-c2010"></a>Chyba kompilátoru C2010

'znak': neočekávalo se v seznamu formálních parametrů makra

Znak je nesprávně použitý v seznamu formálních parametrů v definici makra. Odeberte znak, který má tuto chybu napravíme.

Následující ukázka generuje C2010:

```
// C2010.cpp
// compile with: /c
#define mymacro(a|) (2*a)   // C2010
#define mymacro(a) (2*a)   // OK
```