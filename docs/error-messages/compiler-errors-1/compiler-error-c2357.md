---
title: Chyba kompilátoru C2357
ms.date: 11/04/2016
f1_keywords:
- C2357
helpviewer_keywords:
- C2357
ms.assetid: d1083945-0ea2-4385-9e66-8c665978806c
ms.openlocfilehash: ce1926468bac7e44485be5c0a0944fdf12dce3d8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759916"
---
# <a name="compiler-error-c2357"></a>Chyba kompilátoru C2357

' identifier ': musí být funkce typu ' type '

Váš kód deklaruje verzi funkce `atexit`, která neodpovídá verzi deklarované interně kompilátorem. Deklarujte `atexit` následujícím způsobem:

```
int __cdecl atexit(void (__cdecl *)());
```

Další informace najdete v tématu [init_seg](../../preprocessor/init-seg.md).

Následující ukázka generuje C2357:

```cpp
// C2357.cpp
// compile with: /c
// C2357 expected
#pragma warning(disable : 4075)
// Uncomment the following line to resolve.
// int __cdecl myexit(void (__cdecl *)());
#pragma init_seg(".mine$m",myexit)
```
