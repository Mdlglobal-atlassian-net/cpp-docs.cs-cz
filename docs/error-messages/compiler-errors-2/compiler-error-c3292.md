---
title: Chyba kompilátoru C3292 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3292
dev_langs:
- C++
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8fc5f89978a7ecaff526fa05ca7a47494aada987
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112457"
---
# <a name="compiler-error-c3292"></a>Chyba kompilátoru C3292

obor názvů cli nejde znovu otevřít

Obor názvů cli se nedá deklarovat v kódu.  Další informace najdete v tématu [Platform, default a cli obory názvů](../../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3292.

```
// C3292.cpp
// compile with: /clr /c
namespace cli {};   // C3292
```