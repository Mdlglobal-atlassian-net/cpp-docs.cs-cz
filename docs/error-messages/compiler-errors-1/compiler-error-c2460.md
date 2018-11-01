---
title: Chyba kompilátoru C2460
ms.date: 11/04/2016
f1_keywords:
- C2460
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
ms.openlocfilehash: 414b6e53cf1610a55db984a1127bfc884102494f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589589"
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