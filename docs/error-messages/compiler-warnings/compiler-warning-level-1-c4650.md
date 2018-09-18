---
title: Upozornění (úroveň 1) C4650 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4650
dev_langs:
- C++
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d49b21452465f26d6e696f928c04c20dc0e33307
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052884"
---
# <a name="compiler-warning-level-1-c4650"></a>Kompilátor upozornění (úroveň 1) C4650

informace o ladění není v předkompilovanou hlavičkou; bude k dispozici jenom globální symboly z hlavičky

Soubor předkompilované hlavičky nezkompiloval se pomocí Microsoft symbolické ladicí informace.

V případě propojení, nebude obsahovat výsledný soubor spustitelný soubor nebo dynamická knihovna ladicí informace pro místní symboly, které jsou obsaženy v předkompilované hlavičce.

Toto upozornění se lze vyvarovat opětovnou kompilací soubor předkompilované hlavičky s [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) možnost příkazového řádku.