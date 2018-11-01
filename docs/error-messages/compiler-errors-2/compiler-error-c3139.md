---
title: Chyba kompilátoru C3139
ms.date: 11/04/2016
f1_keywords:
- C3139
helpviewer_keywords:
- C3139
ms.assetid: 95c92263-10ac-4ff3-b385-6312dd92adbc
ms.openlocfilehash: f224be74a94e0e769e7c26bc99b4790d69f6b65b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521200"
---
# <a name="compiler-error-c3139"></a>Chyba kompilátoru C3139

'struct': nejde vyexportovat UDT bez členů

Jste se pokusili použít [exportovat](../../windows/export.md) atribut prázdný UDT (uživatelem definovaný typ). Příklad:

```
// C3139.cpp
#include "unknwn.h"
[emitidl];
[module(name=xx)];

[export] struct MyStruct {   // C3139 empty type
};
int main(){}
```