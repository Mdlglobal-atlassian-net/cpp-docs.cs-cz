---
title: Kompilátor upozornění (úroveň 1) C4276
ms.date: 11/04/2016
f1_keywords:
- C4276
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
ms.openlocfilehash: 87f13f7da12a3f7e40aaad180e2a3bc83e121771
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586911"
---
# <a name="compiler-warning-level-1-c4276"></a>Kompilátor upozornění (úroveň 1) C4276

'function': žádný prototyp k dispozici; předpokládá, že žádné parametry.

Když převzít adresu funkce s [__stdcall](../../cpp/stdcall.md) konvence volání, je třeba zadat prototyp, kompilátor může vytvořit upravený název funkce. Protože *funkce* nemá žádný prototyp, kompilátor při vytváření upravený název, předpokládá funkce nemá žádné parametry.