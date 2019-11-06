---
title: Upozornění kompilátoru (úroveň 1) C4091
ms.date: 11/04/2016
f1_keywords:
- C4091
helpviewer_keywords:
- C4091
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
ms.openlocfilehash: ce6dd980ef70f129a0dbae474b8f717f7573f861
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626742"
---
# <a name="compiler-warning-level-1-c4091"></a>Upozornění kompilátoru (úroveň 1) C4091

klíčové slovo: ignoruje se vlevo od typu, pokud není deklarovaná žádná proměnná.

Kompilátor zjistil situaci, kdy uživatel pravděpodobně určil proměnnou, která má být deklarována, ale kompilátor nedokázal deklarovat proměnnou.

## <a name="example"></a>Příklad

Atribut `__declspec` na začátku deklarace uživatelsky definovaného typu platí pro proměnnou daného typu. C4091 značí, že není deklarována žádná proměnná. Následující ukázka generuje C4091.

```cpp
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

Pokud je identifikátor typu typedef, nemůže být zároveň názvem proměnné. Následující ukázka generuje C4091.

```cpp
// C4091_b.cpp
// compile with: /c /W1 /WX
#define LIST 4
typedef struct _LIST {} LIST;   // C4091
```