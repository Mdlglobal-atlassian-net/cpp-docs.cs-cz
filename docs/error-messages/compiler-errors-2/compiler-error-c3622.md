---
title: Chyba kompilátoru C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: 69565a1a2d159623bca927a94543834d18c13299
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518089"
---
# <a name="compiler-error-c3622"></a>Chyba kompilátoru C3622

'class': pro třídu deklarovanou jako '– klíčové slovo' nelze vytvořit instanci

Byl proveden pokus o vytvoření instance třídy označené jako [abstraktní](../../windows/abstract-cpp-component-extensions.md). Třída označena jako `abstract` může být základní třídy, ale nemůže být vytvořena instance.

## <a name="example"></a>Příklad

Následující ukázka generuje C3622.

```
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```
