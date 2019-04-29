---
title: Kompilátor upozornění (úroveň 4) C4457
ms.date: 11/04/2016
f1_keywords:
- C4457
helpviewer_keywords:
- C4457
ms.assetid: 02fd149a-917d-4f67-97a6-eb714572271f
ms.openlocfilehash: 11307ddc3b13a9cd9b36f1ee927082104792b07f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391436"
---
# <a name="compiler-warning-level-4-c4457"></a>Kompilátor upozornění (úroveň 4) C4457

> deklarace "*identifikátor*' skryje parametr funkce

Deklarace *identifikátor* v místním oboru skrývá deklaraci parametru identicky pojmenované funkce. Toto upozornění umožňuje zjistit, která odkazuje na *identifikátor* v místním oboru vyřešit lokálně deklarované verzi, ne parametr, který může nebo nemusí být vašich představ. Chcete-li vyřešit tento problém, doporučujeme že poskytnout lokální proměnné s názvy, které nejsou v rozporu s názvy parametrů.

## <a name="example"></a>Příklad

Následující ukázka generuje C4457, protože parametr `x` a místní proměnnou `x` v `member_fn` mají stejné názvy. Chcete-li vyřešit tento problém, použijte jiné názvy parametrů a lokálních proměnných.

```cpp
// C4457_hide.cpp
// compile with: cl /W4 /c C4457_hide.cpp

struct S {
    void member_fn(unsigned x) {
        double a = 0;
        for (int x = 0; x < 10; ++x) {  // C4457
            a += x; // uses local x
        }
        a += x; // uses parameter x
    }
} s;
```
