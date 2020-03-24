---
title: Upozornění kompilátoru (úroveň 1) C4650
ms.date: 11/04/2016
f1_keywords:
- C4650
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
ms.openlocfilehash: e57f1d9acba4a8734339f3b8e538120abe542efc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199565"
---
# <a name="compiler-warning-level-1-c4650"></a>Upozornění kompilátoru (úroveň 1) C4650

informace o ladění nejsou v předkompilované hlavičce; k dispozici jsou jenom globální symboly z hlavičky.

Soubor předkompilované hlavičky nebyl zkompilován s informacemi o symbolickém ladění společnosti Microsoft.

V případě propojení nebude výsledný spustitelný soubor nebo soubor dynamické knihovny obsahovat informace o ladění místních symbolů obsažených v předkompilované hlavičce.

Toto upozornění se může vyhnout tím, že znovu zkompiluje soubor předkompilované hlavičky s možností příkazového řádku [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) .
