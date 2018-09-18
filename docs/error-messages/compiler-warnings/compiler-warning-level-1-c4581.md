---
title: Upozornění (úroveň 1) C4581 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4581
dev_langs:
- C++
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 586283e41fb38baae828bf5a4380ec2afe323ecb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116045"
---
# <a name="compiler-warning-level-1-c4581"></a>Kompilátor upozornění (úroveň 1) C4581

zastaralé chování: "Řetězec1" nahradit "řetězec2" atributu procesu

Tuto chybu mohou být generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual C++ 2005: kontroly parametrů pro atributy Visual C++.

V předchozích verzích byla přijata hodnoty atributů, zda byl uzavřen do uvozovek. Pokud je hodnota výčtu, nesmí být uzavřen v uvozovkách.

## <a name="example"></a>Příklad

Následující ukázka generuje C4581.

```
// C4581.cpp
// compile with: /c /W1
#include "unknwn.h"
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI : IUnknown {};

[coclass, uuid(12345678-1111-2222-3333-123456789012), threading("free")]   // C4581
// try the following line instead
// [coclass, uuid(12345678-1111-2222-3333-123456789012), threading(free)]
class CSample : public IMyI {};
```