---
title: Upozornění (úroveň 1) C4920 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4920
dev_langs:
- C++
helpviewer_keywords:
- C4920
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4873fcb1e5bb6d712e44b86d6f60589d6c8ddf4d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091735"
---
# <a name="compiler-warning-level-1-c4920"></a>Kompilátor upozornění (úroveň 1) C4920

člen výčtu člen výčtu = už zjistil ve výčtu výčtového typu jako člen value = value

Pokud .tlb, který můžete předat #import má stejné symbol definovaný ve dvou nebo více výčty, toto upozornění signalizuje, že následné stejné symboly jsou ignorovány a bude okomentován navýšení kapacity v souboru .tlh.

Za předpokladu, že .tlb, který obsahuje:

```
library MyLib
{
    typedef enum {
        enumMember = 512
    } AProblem;

    typedef enum {
        enumMember = 1024
    } BProblem;
};
```

Následující ukázky generuje C4920,

```
// C4920.cpp
// compile with: /W1
#import "t4920.tlb"   // C4920

int main() {
}
```