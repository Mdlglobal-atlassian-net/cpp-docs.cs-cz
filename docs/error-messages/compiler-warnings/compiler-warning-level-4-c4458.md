---
title: Kompilátor upozornění (úroveň 4) C4458
ms.date: 11/04/2016
f1_keywords:
- C4458
helpviewer_keywords:
- C4458
ms.assetid: 7bdaa1b1-0caf-4d68-98c4-6bdd441c23fb
ms.openlocfilehash: 9e5eb8dc44968332abc097bfbd16b48e3240695c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391449"
---
# <a name="compiler-warning-level-4-c4458"></a>Kompilátor upozornění (úroveň 4) C4458

> deklarace "*identifikátor*' skryje člen třídy

Deklarace *identifikátor* v místním oboru skrývá deklaraci nazvanými *identifikátor* v oboru třídy. Toto upozornění umožňuje zjistit, která odkazuje na *identifikátor* v tomto oboru vyřešit lokálně deklarované verzi není verze člena třídy, který může nebo nemusí být vaším záměrem. Chcete-li vyřešit tento problém, doporučujeme že poskytnout lokální proměnné s názvy, které nejsou v rozporu s názvy členů třídy.

## <a name="example"></a>Příklad

Následující ukázka generuje C4458, protože parametr `x` a místní proměnnou `y` v `member_fn` mají stejné názvy jako datové členy třídy. Chcete-li vyřešit tento problém, použijte jiné názvy parametrů a lokálních proměnných.

```cpp
// C4458_hide.cpp
// compile with: cl /W4 /c C4458_hide.cpp

struct S {
    int x;
    float y;
    void member_fn(long x) {   // C4458
        double y;  // C4458
        y = x;
        // To fix this issue, change the parameter name x
        // and local name y to something that does not
        // conflict with the data member names.
    }
} s;
```
