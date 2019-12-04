---
title: Chyba kompilátoru C2504
ms.date: 11/04/2016
f1_keywords:
- C2504
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
ms.openlocfilehash: d47d99962d089d873cb9bbdf9baac7eab706fc16
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746887"
---
# <a name="compiler-error-c2504"></a>Chyba kompilátoru C2504

' class ': nedefinovaná základní třída

Základní třída je deklarována, ale nebyla definována.  Možné příčiny:

1. Chybějící soubor k zahrnutí

1. Externí základní třída není deklarovaná s [extern](../../cpp/using-extern-to-specify-linkage.md).

Následující ukázka generuje C2504:

```cpp
// C2504.cpp
// compile with: /c
class A;
class B : public A {};   // C2504
```

Ok

```
class C{};
class D : public C {};
```
