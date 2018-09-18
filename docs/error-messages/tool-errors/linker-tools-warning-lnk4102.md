---
title: Upozornění Linkerů LNK4102 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4102
dev_langs:
- C++
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9daaffc4ddfa9a869c2e60e2c05dc2b7e296d94b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031851"
---
# <a name="linker-tools-warning-lnk4102"></a>Upozornění linkerů LNK4102

Export odstraňující destruktor "name"; bitové kopie se možná správně nespustí

Program se pokusil exportovat odstraňování destruktor. Výsledný odstranění může dojít k přes hranice knihovny DLL tak, aby proces může uvolnit paměť, která není vlastníkem. Ujistěte se, že daný symbol není uvedená v souboru .def a že symbol není uvedena jako argument **/IMPORT** nebo **/EXPORT** možnost příkazového řádku linkeru.

Pokud bude probíhat opětovné sestavení knihovny run-time jazyka C, můžete tuto zprávu ignorovat.