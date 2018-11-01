---
title: Chyba kompilátoru C3551
ms.date: 11/04/2016
f1_keywords:
- C3551
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
ms.openlocfilehash: 9dfdee155e85bd772ed1d4ce22c525f8a4c79f5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458744"
---
# <a name="compiler-error-c3551"></a>Chyba kompilátoru C3551

"očekává, že že pozdně zadaný návratový typ"

Pokud používáte `auto` – klíčové slovo jako zástupný symbol pro návratový typ funkce, je nutné zadat pozdně zadaný návratový typ. V následujícím příkladu je pozdně zadaný návratový typ funkce `myFunction` je ukazatel na pole čtyři prvky typu `int`.

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>Viz také

[auto](../../cpp/auto-cpp.md)