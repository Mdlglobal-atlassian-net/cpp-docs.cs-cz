---
title: Chyba kompilátoru C2181 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2181
dev_langs:
- C++
helpviewer_keywords:
- C2181
ms.assetid: d52b2fe4-566a-40a9-b8e2-8dce1f287668
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d449bb011b63034df49fe4e3d13b373e0ca2c827
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062277"
---
# <a name="compiler-error-c2181"></a>Chyba kompilátoru C2181

Neplatné else bez odpovídajícího if

Každý `else` musí mít odpovídající `if`.

Následující ukázka generuje C2181:

```
// C2181.cpp
int main() {
   int i = 0;
   else   // C2181
      i = 1;
}
```

Možná řešení:

```
// C2181b.cpp
int main() {
   int i = 0;
   if(i)
      i = 0;
   else
      i = 1;
}
```