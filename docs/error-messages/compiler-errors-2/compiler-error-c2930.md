---
title: Chyba kompilátoru C2930
ms.date: 11/04/2016
f1_keywords:
- C2930
helpviewer_keywords:
- C2930
ms.assetid: f07eecd1-e5d1-4518-bd89-b1fd2a003a17
ms.openlocfilehash: b30e614236298cf9a07cbc29e028039903f9748f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760977"
---
# <a name="compiler-error-c2930"></a>Chyba kompilátoru C2930

' class ': typ-class-ID se předefinovalo jako enumerátor identifikátoru Enum

Nelze použít obecnou třídu nebo třídu šablony jako člen výčtu.

Tato chyba může být způsobena nesprávným spárováním složených závorek.

Následující ukázka generuje C2930:

```cpp
// C2930.cpp
// compile with: /c
template<class T>
class x{};
enum SomeEnum { x };   // C2930

class y{};
enum SomeEnum { y };
```

C2930 může také nastat při použití generických typů:

```cpp
// C2930c.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
enum SomeEnum { GC };   // C2930

ref struct GC2 {};
enum SomeEnum2 { GC2 };
```
