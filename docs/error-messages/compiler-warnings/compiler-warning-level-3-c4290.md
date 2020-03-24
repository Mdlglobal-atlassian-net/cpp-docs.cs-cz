---
title: Upozornění kompilátoru (úroveň 3) C4290
ms.date: 11/04/2016
f1_keywords:
- C4290
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
ms.openlocfilehash: 5970aa439a450bda4c1a2036da299d5c3cfbdb7a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198897"
---
# <a name="compiler-warning-level-3-c4290"></a>Upozornění kompilátoru (úroveň 3) C4290

C++specifikace výjimky se ignoruje s výjimkou označující, že funkce není __declspec (nethrow).

Funkce je deklarována pomocí specifikace výjimky, kterou vizuál C++ přijímá, ale neimplementuje. Kód se specifikacemi výjimek, které jsou ignorovány během kompilace, může být nutné znovu zkompilovat a propojit se v budoucích verzích, které podporují specifikace výjimek.

Další informace naleznete v tématu [Specifikace výjimek (throw)](../../cpp/exception-specifications-throw-cpp.md) .

Tomuto upozornění se můžete vyhnout pomocí direktivy pragma [Warning](../../preprocessor/warning.md) :

```cpp
#pragma warning( disable : 4290 )
```

Následující ukázka kódu generuje C4290:

```cpp
// C4290.cpp
// compile with: /EHs /W3 /c
void f1(void) throw(int) {}   // C4290

// OK
void f2(void) throw() {}
void f3(void) throw(...) {}
```
