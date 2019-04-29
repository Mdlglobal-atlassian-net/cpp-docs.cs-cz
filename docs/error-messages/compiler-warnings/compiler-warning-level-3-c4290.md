---
title: Kompilátor upozornění (úroveň 3) C4290
ms.date: 11/04/2016
f1_keywords:
- C4290
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
ms.openlocfilehash: c585294686298a1197d437d41a0d541f1268985f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402083"
---
# <a name="compiler-warning-level-3-c4290"></a>Kompilátor upozornění (úroveň 3) C4290

C++Specifikace výjimky se ignoruje s výjimkou, že funkce není not __declspec(nothrow).

Funkce je deklarovaná pomocí specifikace výjimky, která přijímá Visual C++, ale neimplementuje. Kódování s výjimku, kterou specifikace, které jsou ignorovány při kompilaci může muset být překompilovány a propojené bude znovu použít v budoucích verzích podporuje specifikace výjimek.

Další informace najdete v tématu [specifikace výjimek (throw)](../../cpp/exception-specifications-throw-cpp.md) .

Toto upozornění můžete vyhnout použitím [upozornění](../../preprocessor/warning.md) – Direktiva pragma:

```
#pragma warning( disable : 4290 )
```

Následující ukázka kódu generuje C4290:

```
// C4290.cpp
// compile with: /EHs /W3 /c
void f1(void) throw(int) {}   // C4290

// OK
void f2(void) throw() {}
void f3(void) throw(...) {}
```