---
title: Kompilátor upozornění (úroveň 4) C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: 80ad388b26b2b972aa1301c1f335d0361a75f15f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559835"
---
# <a name="compiler-warning-level-4-c4235"></a>Kompilátor upozornění (úroveň 4) C4235

používá se nestandardní rozšíření: klíčové slovo '– klíčové slovo' není na této architektuře podporováno

Kompilátor nepodporuje klíčové slovo, které jste použili.

Toto upozornění je automaticky povýšen na chybu. Pokud chcete toto chování upravit, použijte [varování #pragma](../../preprocessor/warning.md). Například chcete-li C4235 do upozornění úrovně 2, použijte následující řádek kódu

```
#pragma warning(2:4235)
```

v souboru zdrojového kódu.