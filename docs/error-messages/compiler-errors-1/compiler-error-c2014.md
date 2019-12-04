---
title: Chyba kompilátoru C2014
ms.date: 11/04/2016
f1_keywords:
- C2014
helpviewer_keywords:
- C2014
ms.assetid: 231d8e9c-48c0-4027-99a3-245d186275ec
ms.openlocfilehash: 6c7e941970415c933b38f35b6c09247a3c0fd411
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757394"
---
# <a name="compiler-error-c2014"></a>Chyba kompilátoru C2014

příkaz preprocesoru musí být spuštěný jako první neprázdný znak.

`#` znaménko direktivy preprocesoru musí být prvním znakem na řádku, který není prázdný znak.

Následující ukázka generuje C2014:

```cpp
// C2014.cpp
int k; #include <stdio.h>   // C2014
```

Možné řešení:

```cpp
// C2014b.cpp
// compile with: /c
int k;
#include <stdio.h>
```
