---
title: Chyba kompilátoru C3622 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3622
dev_langs:
- C++
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13ba39a2baf9da2039bbc97fe459f8840effacea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062407"
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
