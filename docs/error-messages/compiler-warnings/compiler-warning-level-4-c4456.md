---
title: Upozornění (úroveň 4) C4456 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4456
dev_langs:
- C++
helpviewer_keywords:
- C4456
ms.assetid: 5ab39fc1-0e19-461b-842b-4da80560b044
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ab6939fe37260b906a43c4e2ff6683733348952
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039891"
---
# <a name="compiler-warning-level-4-c4456"></a>Kompilátor upozornění (úroveň 4) C4456

> deklarace "*identifikátor*' skryje předchozí místní deklaraci

Deklarace *identifikátor* v místním oboru skrývá deklaraci předchozí místní deklaraci se stejným názvem. Toto upozornění umožňuje zjistit, která odkazuje na *identifikátor* v místním oboru vyřešit lokálně deklarované verzi není předchozí místní, který může nebo nemusí být vašich představ. Chcete-li vyřešit tento problém, doporučujeme že poskytnout lokální proměnné s názvy, které nejsou v rozporu s názvy jiných místní.

## <a name="example"></a>Příklad

Následující ukázka generuje C4456, protože řídit proměnná smyčky `int x` a místní proměnnou `double x` v `member_fn` mají stejné názvy. Chcete-li vyřešit tento problém, použijte jiné názvy pro místní proměnné.

```cpp
// C4456_hide.cpp
// compile with: cl /W4 /c C4456_hide.cpp

struct S {
    void member_fn(unsigned u) {
        double x = 0;
        for (int x = 0; x < 10; ++x) {  // C4456
            u += x; // uses local int x
        }
        x += u; // uses local double x
    }
} s;
```
