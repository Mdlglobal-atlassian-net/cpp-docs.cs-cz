---
title: Upozornění linkerů LNK4102
ms.date: 11/04/2016
f1_keywords:
- LNK4102
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
ms.openlocfilehash: 0f9c8649988dd3056e98730ac4b02022a8c9dd51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643089"
---
# <a name="linker-tools-warning-lnk4102"></a>Upozornění linkerů LNK4102

Export odstraňující destruktor "name"; bitové kopie se možná správně nespustí

Program se pokusil exportovat odstraňování destruktor. Výsledný odstranění může dojít k přes hranice knihovny DLL tak, aby proces může uvolnit paměť, která není vlastníkem. Ujistěte se, že daný symbol není uvedená v souboru .def a že symbol není uvedena jako argument **/IMPORT** nebo **/EXPORT** možnost příkazového řádku linkeru.

Pokud bude probíhat opětovné sestavení knihovny run-time jazyka C, můžete tuto zprávu ignorovat.