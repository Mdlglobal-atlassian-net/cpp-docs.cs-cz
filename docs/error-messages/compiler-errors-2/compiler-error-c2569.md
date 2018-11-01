---
title: Chyba kompilátoru C2569
ms.date: 11/04/2016
f1_keywords:
- C2569
helpviewer_keywords:
- C2569
ms.assetid: 092bed1e-f631-436c-9586-7750629f6fac
ms.openlocfilehash: 1344bd8bde532d2e813ca03e173b995e935c76b2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661315"
---
# <a name="compiler-error-c2569"></a>Chyba kompilátoru C2569

'EnumOrUnion': výčet/sjednocení nejde použít jako základní třídu

Pokud typ musí být odvozen ze zadaného unie nebo výčtu, změňte na třída nebo struktura, unie nebo výčtu.

Následující ukázka generuje C2569:

```
// C2569.cpp
// compile with: /c
union ubase {};
class cHasPubUBase : public ubase {};   // C2569
// OK
struct sbase {};
class cHasPubUBase : public sbase {};
```