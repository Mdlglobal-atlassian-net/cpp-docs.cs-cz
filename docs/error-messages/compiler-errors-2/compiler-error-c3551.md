---
title: Chyba kompilátoru C3551
ms.date: 11/04/2016
f1_keywords:
- C3551
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
ms.openlocfilehash: 48b378eb734c5830bedbf417d99d34955e2e6d0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375974"
---
# <a name="compiler-error-c3551"></a>Chyba kompilátoru C3551

"očekává, že že pozdně zadaný návratový typ"

Pokud používáte `auto` – klíčové slovo jako zástupný symbol pro návratový typ funkce, je nutné zadat pozdně zadaný návratový typ. V následujícím příkladu je pozdně zadaný návratový typ funkce `myFunction` je ukazatel na pole čtyři prvky typu `int`.

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>Viz také:

[auto](../../cpp/auto-cpp.md)