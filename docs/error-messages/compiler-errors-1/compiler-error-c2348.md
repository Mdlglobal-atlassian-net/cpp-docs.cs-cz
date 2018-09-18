---
title: Chyba kompilátoru C2348 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2348
dev_langs:
- C++
helpviewer_keywords:
- C2348
ms.assetid: 4c4d701f-ccf1-46fe-9ddb-3f341684f269
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7d30253e23fd22ae721268f94a0fecf158a68c3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104995"
---
# <a name="compiler-error-c2348"></a>Chyba kompilátoru C2348

'type name': není agregací C-style, nejde exportovat ve vloženém IDL

Umístit `struct` v souboru IDL se [exportovat](../../windows/export.md) atribut, `struct` musí obsahovat pouze data.

Následující ukázka generuje C2348:

```
// C2348.cpp
// C2348 error expected
[ module(name="SimpleMidlTest") ];

[export]
struct Point {
   // Delete the following two lines to resolve.
   Point() : m_i(0), m_j(0) {}
   Point(int i, int j) : m_i(i), m_j(j) {}

   int m_i;
   int m_j;
};
```