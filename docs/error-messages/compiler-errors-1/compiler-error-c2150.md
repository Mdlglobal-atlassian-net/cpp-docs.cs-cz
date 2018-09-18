---
title: Chyba kompilátoru C2150 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2150
dev_langs:
- C++
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef0920c98fe59fe5bca49bba4c62a486a61c0a55
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024707"
---
# <a name="compiler-error-c2150"></a>Chyba kompilátoru C2150

> "*identifikátor*': bitové pole musí mít typ int,"signed int"nebo"int bez znaménka.

Základní typ bitového pole musí být `int`, `signed int`, nebo `unsigned int`.

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak můžete setkat C2150 a jak ho opravit:

```cpp
// C2150.cpp
// compile with: /c
struct A {
   float a : 8;    // C2150
   int i : 8;      // OK
};
```