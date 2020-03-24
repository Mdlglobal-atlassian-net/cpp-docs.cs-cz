---
title: Upozornění kompilátoru (úroveň 1) C4186
ms.date: 11/04/2016
f1_keywords:
- C4186
helpviewer_keywords:
- C4186
ms.assetid: caf3f7d8-f305-426b-8d4e-2b96f5c269ea
ms.openlocfilehash: 6772e384b5908cbe81f85758f86eabe4c8240e6a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163320"
---
# <a name="compiler-warning-level-1-c4186"></a>Upozornění kompilátoru (úroveň 1) C4186

\#import atributu ' Attribute ' vyžaduje argumenty Count; přeskočen

Atribut `#import` má nesprávný počet argumentů.

## <a name="example"></a>Příklad

```cpp
// C4186.cpp
// compile with: /W1 /c
#import "stdole2.tlb" no_namespace("abc") rename("a","b","c")  // C4186
```

Atribut `no_namespace` nepřijímá žádné argumenty. Atribut **přejmenování** přijímá pouze dva argumenty.
