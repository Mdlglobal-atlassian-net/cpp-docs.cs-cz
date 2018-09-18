---
title: Chyba kompilátoru C2460 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2460
dev_langs:
- C++
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb2d85ffbc7aa799f0688fbb10021a04ef9455ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022611"
---
# <a name="compiler-error-c2460"></a>Chyba kompilátoru C2460

'identifier1': používá "identifier2", které se zrovna definuje

Třídu nebo strukturu (`identifier2`) je deklarován jako člena sebe sama (`identifier1`). Nejsou povoleny rekurzivní definice tříd a struktur.

Následující ukázka generuje C2460:

```
// C2460.cpp
class C {
   C aC;    // C2460
};
```

Místo toho použijte odkaz na ukazatel ve třídě.

```
// C2460.cpp
class C {
   C * aC;    // OK
};
```