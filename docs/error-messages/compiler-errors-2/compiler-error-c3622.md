---
title: Chyba kompilátoru C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: ed307f46db1261d79d5b0ec6b36852cac2e6d13e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222006"
---
# <a name="compiler-error-c3622"></a>Chyba kompilátoru C3622

'class': pro třídu deklarovanou jako '– klíčové slovo' nelze vytvořit instanci

Byl proveden pokus o vytvoření instance třídy označené jako [abstraktní](../../extensions/abstract-cpp-component-extensions.md). Třída označena jako `abstract` může být základní třídy, ale nemůže být vytvořena instance.

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
