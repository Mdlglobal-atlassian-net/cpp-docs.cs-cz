---
title: Compiler Error C2936
ms.date: 11/04/2016
f1_keywords:
- C2936
helpviewer_keywords:
- C2936
ms.assetid: 5d1ba0fc-0c78-4a37-a83b-1ef8527763be
ms.openlocfilehash: 547690302661656cc5368f5969432de68ac91e3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302953"
---
# <a name="compiler-error-c2936"></a>Compiler Error C2936

'class': typ třídy id se předefinovalo jako proměnnou globálních dat

Rozvrhy generic nebo šablony třídy nelze použít jako globální data proměnnou.

Tato chyba může nastat, pokud jsou nesprávně odpovídající složené závorky.

Následující ukázka generuje C2936:

```
// C2936.cpp
// compile with: /c
template<class T> struct TC { };
int TC<int>;   // C2936

// OK
struct TC2 { };
int TC2;
```

C2936 může dojít také při použití obecných typů:

```
// C2936b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
int GC<int>;   // C2936

// OK
ref struct GC2 {};
int GC2;
```