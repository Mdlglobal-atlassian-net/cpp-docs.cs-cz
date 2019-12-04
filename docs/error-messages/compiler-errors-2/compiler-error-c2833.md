---
title: Chyba kompilátoru C2833
ms.date: 11/04/2016
f1_keywords:
- C2833
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
ms.openlocfilehash: c1467a3c67cccf28cc6b9bd0f987fe77b8da8988
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757875"
---
# <a name="compiler-error-c2833"></a>Chyba kompilátoru C2833

operátor Operator není rozpoznaným operátorem nebo typem.

Po `operator` slova musí následovat operátor, který chcete přepsat, nebo typ, který chcete převést.

Seznam operátorů, které lze definovat ve spravovaném typu, naleznete v tématu [operátory definované uživatelem](../../dotnet/user-defined-operators-cpp-cli.md).

Následující ukázka generuje C2833:

```cpp
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```
