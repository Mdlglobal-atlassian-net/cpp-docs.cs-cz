---
title: Chyba kompilátoru C2460
ms.date: 11/04/2016
f1_keywords:
- C2460
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
ms.openlocfilehash: a7d20a7658a75a492e19b9e81acaa3b6fce5cae7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743936"
---
# <a name="compiler-error-c2460"></a>Chyba kompilátoru C2460

' identifier1 ': používá ' identifier2 ', které je právě definováno

Třída nebo struktura (`identifier2`) je deklarována jako člen sebe sama (`identifier1`). Rekurzivní definice tříd a struktur nejsou povoleny.

Následující ukázka generuje C2460:

```cpp
// C2460.cpp
class C {
   C aC;    // C2460
};
```

Místo toho použijte odkaz na ukazatel ve třídě.

```cpp
// C2460.cpp
class C {
   C * aC;    // OK
};
```
