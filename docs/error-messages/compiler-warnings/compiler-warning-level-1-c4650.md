---
title: Kompilátor upozornění (úroveň 1) C4650
ms.date: 11/04/2016
f1_keywords:
- C4650
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
ms.openlocfilehash: ea3f1b6e792239692960e74c8360c6c3a1323815
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536097"
---
# <a name="compiler-warning-level-1-c4650"></a>Kompilátor upozornění (úroveň 1) C4650

informace o ladění není v předkompilovanou hlavičkou; bude k dispozici jenom globální symboly z hlavičky

Soubor předkompilované hlavičky nezkompiloval se pomocí Microsoft symbolické ladicí informace.

V případě propojení, nebude obsahovat výsledný soubor spustitelný soubor nebo dynamická knihovna ladicí informace pro místní symboly, které jsou obsaženy v předkompilované hlavičce.

Toto upozornění se lze vyvarovat opětovnou kompilací soubor předkompilované hlavičky s [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) možnost příkazového řádku.