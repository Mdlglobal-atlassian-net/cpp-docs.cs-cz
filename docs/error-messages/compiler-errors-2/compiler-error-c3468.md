---
title: Chyba kompilátoru C3468 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3468
dev_langs:
- C++
helpviewer_keywords:
- C3468
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ccd7238fa7101f70ce2e15a6cd39030934901fb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023953"
---
# <a name="compiler-error-c3468"></a>Chyba kompilátoru C3468

'type': Typ může předávat pouze na sestavení:

"`file`' není sestavení.

Může být přeposílán pouze typy v sestavení.

Další informace najdete v tématu [předávání typů (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md).

## <a name="example"></a>Příklad

Následující příklad vytvoří modul.

```
// C3468.cpp
// compile with: /LN /clr
public ref class R {};
```

## <a name="example"></a>Příklad

Následující ukázka generuje C3468.

```
// C3468_b.cpp
// compile with: /clr /c
#using "C3468.netmodule"
[ assembly:TypeForwardedTo(R::typeid) ];   // C3468
```