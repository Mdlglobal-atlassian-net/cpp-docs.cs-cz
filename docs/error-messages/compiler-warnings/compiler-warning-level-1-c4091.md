---
title: Kompilátor upozornění (úroveň 1) C4091
ms.date: 11/04/2016
f1_keywords:
- C4091
helpviewer_keywords:
- C4091
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
ms.openlocfilehash: 87432a74dfe7c09a52f436d4e91b3f70eb66856b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410444"
---
# <a name="compiler-warning-level-1-c4091"></a>Kompilátor upozornění (úroveň 1) C4091

! – klíčové slovo': ignorovány levá strana 'type', pokud není deklarovaná žádná proměnná

Kompilátor zjistil situace, kdy uživatel pravděpodobně určené proměnnou deklarovat, ale kompilátor nebyl schopen deklarovat proměnnou.

## <a name="example"></a>Příklad

A `__declspec` atribut na začátku deklarace uživatelského typu platí pro proměnnou daného typu. C4091 označuje, že není deklarovaná žádná proměnná. Následující ukázka generuje C4091.

```
// C4091.cpp
// compile with: /W1 /c
__declspec(dllimport) class X {}; // C4091

// __declspec attribute applies to varX
__declspec(dllimport) class X2 {} varX;

// __declspec attribute after the class or struct keyword
// applies to user defined type
class __declspec(dllimport) X3 {};
```

## <a name="example"></a>Příklad

Pokud identifikátor je definice typu, nemůže být také název proměnné. Následující ukázka generuje C4091.

```
// C4091_b.cpp
// compile with: /c /W1 /WX
#define LIST 4
typedef struct _LIST {} LIST;   // C4091
```