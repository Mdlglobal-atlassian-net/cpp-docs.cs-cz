---
title: Upozornění kompilátoru (úroveň 1) C4612
ms.date: 08/27/2018
f1_keywords:
- C4612
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
ms.openlocfilehash: f9478caef9eaba9c72dc282179100daf2d94c6d5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185981"
---
# <a name="compiler-warning-level-1-c4612"></a>Upozornění kompilátoru (úroveň 1) C4612

> Chyba v souboru include filename

## <a name="remarks"></a>Poznámky

K tomuto upozornění dochází u **#pragma include_alias** , pokud název souboru není správný nebo chybí.

Argumenty příkazu **#pragma include_alias** mohou použít formulář nabídky ("*filename*") nebo tvar lomené závorky (\<*filename*>), ale oba musí používat stejný formulář.

## <a name="example"></a>Příklad

```cpp
// C4612.cpp
// compile with: /W1 /LD
#pragma include_alias("StandardIO", <stdio.h>) // C4612
```
