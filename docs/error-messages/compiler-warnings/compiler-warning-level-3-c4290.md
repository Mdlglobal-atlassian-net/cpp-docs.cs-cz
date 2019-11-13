---
title: Upozornění kompilátoru (úroveň 3) C4290
ms.date: 11/04/2016
f1_keywords:
- C4290
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
ms.openlocfilehash: 5ccacd7d5f4dfd2e9ad8de3958d7aa43571091fe
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051654"
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