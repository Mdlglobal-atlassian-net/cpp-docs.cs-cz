---
title: Chyba kompilátoru C3747
ms.date: 11/04/2016
f1_keywords:
- C3747
helpviewer_keywords:
- C3747
ms.assetid: a9a4be67-5d9c-4dcc-9ae9-baae46cbecde
ms.openlocfilehash: 860a990e35b0d51dfc1316a11a2d2512eb40c273
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574354"
---
# <a name="compiler-error-c3747"></a>Chyba kompilátoru C3747

Chybí výchozí parametr typu: Parametr param

Parametry obecného nebo šablonu s výchozími hodnotami nemůže v seznamu parametrů následovat parametry, které nemají výchozí hodnoty.

Následující ukázka generuje C3747:

```
// C3747.cpp
template <class T1 = int, class T2>   // C3747
struct MyStruct {};
```

Možná řešení:

```
// C3747b.cpp
// compile with: /c
template <class T1, class T2 = int>
struct MyStruct {};
```