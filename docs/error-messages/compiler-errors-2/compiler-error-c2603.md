---
title: Chyba kompilátoru C2603 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2603
dev_langs:
- C++
helpviewer_keywords:
- C2603
ms.assetid: 9ca520d0-f082-4b65-933d-17c3bcf8b02c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a893a77fb3760f00fb7fe7b5cb3ce5b3db3346e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057675"
---
# <a name="compiler-error-c2603"></a>Chyba kompilátoru C2603

> "*funkce*': příliš mnoho statických objektů oboru bloku s konstruktory/destruktory ve funkci

Ve verzích kompilátor Visual C++ před Visual Studio 2015 nebo když [/Zc: threadsafeinit](../../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) – možnost kompilátoru je zadán, platí omezení na počet statických objektů v externě viditelné vložená funkce může být 31 .

Chcete-li vyřešit tento problém, doporučujeme přijmout novější verzi sady nástrojů kompilátoru Visual C++, nebo pokud je to možné, remove – možnost kompilátoru/Zc: threadsafeinit. Pokud to není možné, vezměte v úvahu kombinaci statických objektů. Pokud jsou objekty stejného typu, zvažte použití jedné statického pole tohoto typu a odkazovat na jednotlivé členy podle potřeby.

## <a name="example"></a>Příklad

Následující kód vygeneruje C2603 a ukazuje jeden způsob, jak ho opravit:

```cpp
// C2603.cpp
// Compile by using: cl /W4 /c /Zc:threadSafeInit- C2603.cpp
struct C { C() {} };
extern inline void f1() {
    static C C01, C02, C03, C04, C05, C06, C07, C08, C09, C10;
    static C C11, C12, C13, C14, C15, C16, C17, C18, C19, C20;
    static C C21, C22, C23, C24, C25, C26, C27, C28, C29, C30, C31;
    static C C32;   // C2603 Comment this line out to avoid error
}
```
