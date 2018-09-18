---
title: Chyba kompilátoru C3880 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3880
dev_langs:
- C++
helpviewer_keywords:
- C3880
ms.assetid: b0e05d1e-32d0-4034-9246-f37d23573ea9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03cd1c953e4f0183fe71dcbcf4cc3bfb242b4f1c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074354"
---
# <a name="compiler-error-c3880"></a>Chyba kompilátoru C3880

'příkaz var': nelze literální datový člen

Typ [literálu](../../windows/literal-cpp-component-extensions.md) musí být atribut, nebo kompilace lze převést na jednu z následujících typů:

- celočíselný typ

- odkazy řetězců

- výčtu integrálního typu nebo základního typu

Následující ukázka generuje C3880:

```
// C3880.cpp
// compile with: /clr /c
ref struct Y1 {
   literal System::Decimal staticConst1 = 10;   // C3880
   literal int staticConst2 = 10;   // OK
};
```