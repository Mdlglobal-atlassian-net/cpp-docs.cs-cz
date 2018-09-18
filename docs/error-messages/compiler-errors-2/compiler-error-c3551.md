---
title: Chyba kompilátoru C3551 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3551
dev_langs:
- C++
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b45a6f66ab7cf2a5ebb7ae6b2a2f78e664092604
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035731"
---
# <a name="compiler-error-c3551"></a>Chyba kompilátoru C3551

"očekává, že že pozdně zadaný návratový typ"

Pokud používáte `auto` – klíčové slovo jako zástupný symbol pro návratový typ funkce, je nutné zadat pozdně zadaný návratový typ. V následujícím příkladu je pozdně zadaný návratový typ funkce `myFunction` je ukazatel na pole čtyři prvky typu `int`.

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>Viz také

[auto](../../cpp/auto-cpp.md)