---
title: Upozornění linkerů LNK4102
ms.date: 11/04/2016
f1_keywords:
- LNK4102
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
ms.openlocfilehash: 0f9c8649988dd3056e98730ac4b02022a8c9dd51
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327259"
---
# <a name="linker-tools-warning-lnk4102"></a>Upozornění linkerů LNK4102

Export odstraňující destruktor "name"; bitové kopie se možná správně nespustí

Program se pokusil exportovat odstraňování destruktor. Výsledný odstranění může dojít k přes hranice knihovny DLL tak, aby proces může uvolnit paměť, která není vlastníkem. Ujistěte se, že daný symbol není uvedená v souboru .def a že symbol není uvedena jako argument **/IMPORT** nebo **/EXPORT** možnost příkazového řádku linkeru.

Pokud bude probíhat opětovné sestavení knihovny run-time jazyka C, můžete tuto zprávu ignorovat.