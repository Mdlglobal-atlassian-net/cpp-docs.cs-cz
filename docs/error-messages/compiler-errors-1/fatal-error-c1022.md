---
title: Závažná chyba C1022
ms.date: 11/04/2016
f1_keywords:
- C1022
helpviewer_keywords:
- C1022
ms.assetid: edada720-dc73-49bc-bd93-a7945a316312
ms.openlocfilehash: b709d4bd855e38cb3721dec6d09b95ed02454def
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756874"
---
# <a name="fatal-error-c1022"></a>Závažná chyba C1022

očekávané #endif

Direktiva `#if`, `#ifdef`nebo `#ifndef` nemá žádnou vyhovující direktivu `#endif`. Ujistěte se, že každý `#if`, `#ifdef`nebo `#ifndef` má `#endif`pro porovnání.

Následující ukázka generuje C1022:

```cpp
// C1022.cpp
#define true 1

#if (true)
#else
#else    // C1022
```

Možné řešení:

```cpp
// C1022b.cpp
// compile with: /c
#define true 1

#if (true)
#else
#endif
```
