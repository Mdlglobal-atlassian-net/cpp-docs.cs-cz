---
title: Chyba kompilátoru C2930
ms.date: 11/04/2016
f1_keywords:
- C2930
helpviewer_keywords:
- C2930
ms.assetid: f07eecd1-e5d1-4518-bd89-b1fd2a003a17
ms.openlocfilehash: 20fa3e81e66bb30bd63e579a863b6071de4ef871
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385755"
---
# <a name="compiler-error-c2930"></a>Chyba kompilátoru C2930

'class': typ třídy id předefinovalo jako enumerátor "identifikátor výčtu.

Rozvrhy generic nebo šablony třídy nelze použít jako člen výčtu.

Tato chyba může nastat, pokud jsou nesprávně odpovídající složené závorky.

Následující ukázka generuje C2930:

```
// C2930.cpp
// compile with: /c
template<class T>
class x{};
enum SomeEnum { x };   // C2930

class y{};
enum SomeEnum { y };
```

C2930 může dojít také při použití obecných typů:

```
// C2930c.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
enum SomeEnum { GC };   // C2930

ref struct GC2 {};
enum SomeEnum2 { GC2 };
```