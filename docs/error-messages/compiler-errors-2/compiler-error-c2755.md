---
title: Chyba kompilátoru C2755
ms.date: 11/04/2016
f1_keywords:
- C2755
helpviewer_keywords:
- C2755
ms.assetid: 8ee4eeb6-4757-4efe-9100-38ff4a96f1de
ms.openlocfilehash: c2238058dc4b7df6bbe33e98d6ccde996f36b782
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570687"
---
# <a name="compiler-error-c2755"></a>Chyba kompilátoru C2755

'param': beztypový parametr částečné specializace musí být jednoduchý identifikátor.

Beztypový parametr musí být jednoduchý identifikátor, něco, co kompilátor může rozpoznat v době kompilace jednoho identifikátoru nebo konstantní hodnotu.

Následující ukázka generuje C2755:

```
// C2755.cpp
template<int I, int J>
struct A {};

template<int I>
struct A<I,I*5> {};   // C2755
// try the following line instead
// struct A<I,5> {};
```