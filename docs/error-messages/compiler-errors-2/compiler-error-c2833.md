---
title: Chyba kompilátoru C2833
ms.date: 11/04/2016
f1_keywords:
- C2833
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
ms.openlocfilehash: dad6a64f145c3d49d3b43044ea76a11d35827943
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408365"
---
# <a name="compiler-error-c2833"></a>Chyba kompilátoru C2833

'operator operátor' není rozpoznaná jako operátor nebo typ.

Slovo `operator` musí být následován znakem, který chcete přepsat operátor nebo typ, který chcete převést.

Seznam operátorů, které definujete v spravovaného typu, najdete v části [uživatelsky definované operátory](../../dotnet/user-defined-operators-cpp-cli.md).

Následující ukázka generuje C2833:

```
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```