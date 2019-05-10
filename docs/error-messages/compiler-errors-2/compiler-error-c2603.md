---
title: Compiler Error C2603
ms.date: 11/04/2016
f1_keywords:
- C2603
helpviewer_keywords:
- C2603
ms.assetid: 9ca520d0-f082-4b65-933d-17c3bcf8b02c
ms.openlocfilehash: e4540180058c890a1dec9c4060f796f1f044c934
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447993"
---
# <a name="compiler-error-c2603"></a>Compiler Error C2603

> "*funkce*": Příliš mnoho statických objektů oboru bloku s konstruktory/destruktory ve funkci

Ve verzích Microsoft C++ kompilátor před Visual Studio 2015, nebo když [/Zc: threadsafeinit](../../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) – možnost kompilátoru je zadán, je stanovený limit 31 počet statických objektů, které máte v externě viditelné Vložená funkce.

Chcete-li vyřešit tento problém, doporučujeme přijmout novější verze sady Microsoft C++ sada nástrojů kompilátoru, nebo pokud je to možné, remove – možnost kompilátoru/Zc: threadsafeinit. Pokud to není možné, vezměte v úvahu kombinaci statických objektů. Pokud jsou objekty stejného typu, zvažte použití jedné statického pole tohoto typu a odkazovat na jednotlivé členy podle potřeby.

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
