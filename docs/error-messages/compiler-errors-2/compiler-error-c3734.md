---
title: Chyba kompilátoru C3734
ms.date: 11/04/2016
f1_keywords:
- C3734
helpviewer_keywords:
- C3734
ms.assetid: 4e2afdcc-7da9-45a1-9c96-85f25e2986e8
ms.openlocfilehash: 78b3d1a57d358eb11ba2f01ec184c5487a578228
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327922"
---
# <a name="compiler-error-c3734"></a>Chyba kompilátoru C3734

'class': spravované nebo WinRT třída nemůže být coclass

[Coclass](../../windows/coclass.md) atributu nelze použít s spravované nebo třídách WinRT.

Následující ukázka generuje C3734 a ukazuje, jak ho opravit:

```
// C3734.cpp
// compile with: /clr /c
[module(name="x")];

[coclass]
ref class CMyClass {   // C3734 remove the ref keyword to resolve
};
```
