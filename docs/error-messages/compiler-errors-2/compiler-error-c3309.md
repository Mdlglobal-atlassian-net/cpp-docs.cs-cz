---
title: Chyba kompilátoru C3309 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3309
dev_langs:
- C++
helpviewer_keywords:
- C3309
ms.assetid: 75ee16e3-7d4e-4c41-b3cb-64e9849c3aab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7d9d5f80d6c3a32f77637725e8ca53f1fdbfd51
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055478"
---
# <a name="compiler-error-c3309"></a>Chyba kompilátoru C3309

'macro_name': název modulu nemůže být makro ani klíčové slovo

Hodnota, kterou předat vlastnost name atributu modul nemůže být symbol preprocesoru, aby rozbalte; musí být řetězcový literál.

Následující ukázka generuje C3309:

```
// C3309.cpp
#define NAME MyModule
[module(name="NAME")];   // C3309
// Try the following line instead
// [module(name="MyModule")];
[coclass]
class MyClass {
public:
   void MyFunc();
};

int main() {
}
```