---
title: Kompilátor upozornění (úroveň 1) C4651
ms.date: 11/04/2016
f1_keywords:
- C4651
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
ms.openlocfilehash: 01e2472a547e73eda5fcc56952949a0d9611029f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434772"
---
# <a name="compiler-warning-level-1-c4651"></a>Kompilátor upozornění (úroveň 1) C4651

zadaná pro předkompilovanou hlavičku, ale ne pro aktuální kompilaci definice

Definice byl zadán při generování předkompilované hlavičky, ale není v této kompilaci.

Definice, nebudou platit uvnitř předkompilované hlavičky, ale ne ve zbývající části kódu.

Předkompilované hlavičky byl sestaven s /DSYMBOL, kompilátor vygeneruje toto upozornění v případě kompilace/YU nemá /DSYMBOL.  Přidání do příkazového řádku/YU /DSYMBOL řeší toto upozornění.