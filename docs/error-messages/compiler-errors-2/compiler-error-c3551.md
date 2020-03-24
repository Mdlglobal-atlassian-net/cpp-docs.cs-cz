---
title: Chyba kompilátoru C3551
ms.date: 11/04/2016
f1_keywords:
- C3551
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
ms.openlocfilehash: e9a4ce2276a602d59e495a2f336bb9d59dc0cc99
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200756"
---
# <a name="compiler-error-c3551"></a>Chyba kompilátoru C3551

"byl očekáván pozdní zadaný návratový typ"

Použijete-li klíčové slovo `auto` jako zástupný symbol pro návratový typ funkce, je nutné zadat návratový typ s pozdním zadáním. V následujícím příkladu je zpožděný návratový typ funkce `myFunction` ukazatel na pole čtyř prvků typu `int`.

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>Viz také

[auto](../../cpp/auto-cpp.md)
