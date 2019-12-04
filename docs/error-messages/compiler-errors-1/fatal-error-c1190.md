---
title: Závažná chyba C1190
ms.date: 11/04/2016
f1_keywords:
- C1190
helpviewer_keywords:
- C1190
ms.assetid: dee2266d-6c40-4f6e-91db-f01e65f8d2bc
ms.openlocfilehash: 261d25d031d3a11f1d9e25ca3fb2c926cd521f97
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747342"
---
# <a name="fatal-error-c1190"></a>Závažná chyba C1190

spravovaný cílový kód vyžaduje možnost/CLR.

Používáte konstrukce CLR, ale nezadali jste **/CLR**.

Další informace naleznete v tématu [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

Následující ukázka generuje C1190:

```cpp
// C1190.cpp
// compile with: /c
__gc class A {};   // C1190
ref class A {};
```
