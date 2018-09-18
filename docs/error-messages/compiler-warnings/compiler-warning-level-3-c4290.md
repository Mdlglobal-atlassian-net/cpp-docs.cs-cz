---
title: Upozornění (úroveň 3) C4290 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4290
dev_langs:
- C++
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a6f09d8f3396381f34a0fbe3c7150b5948cee01
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46015964"
---
# <a name="compiler-warning-level-3-c4290"></a>Kompilátor upozornění (úroveň 3) C4290

Specifikace výjimky C++ se ignorovala že funkce není not __declspec(nothrow).

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