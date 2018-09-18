---
title: C4094 kompilátoru (úroveň 2) upozornění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4094
dev_langs:
- C++
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b9317cbc31ef8bddb14da11af1087a148fd3188
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078709"
---
# <a name="compiler-warning-level-2-c4094"></a>Kompilátor C4094 upozornění (úroveň 2)

neoznačených "token" nedeklarovalo žádné symboly

Kompilátor zjistil deklaraci prázdný pomocí neoznačených struktury, sjednocení nebo třídy. Deklarace se ignoruje.

## <a name="example"></a>Příklad

```
// C4094.cpp
// compile with: /W2
struct
{
};   // C4094

int main()
{
}
```

Tato podmínka dojde k chybě v části kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).