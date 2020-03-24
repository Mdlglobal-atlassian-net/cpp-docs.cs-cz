---
title: Upozornění kompilátoru (úroveň 1) C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 6408185c99a54d5411fa5b1058cd5ec09d3326d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176309"
---
# <a name="compiler-warning-level-1-c4124"></a>Upozornění kompilátoru (úroveň 1) C4124

__fastcall s kontrolou zásobníku je neefektivní.

Klíčové slovo `__fastcall` bylo použito s povolenou kontrolou zásobníku.

`__fastcall` konvence generuje rychlejší kód, ale Kontrola zásobníku způsobuje pomalejší kód. Při použití `__fastcall`vypněte kontrolu zásobníku pomocí direktivy pragma **check_stack** nebo/GS.

Toto upozornění se vydá jenom pro první funkci deklarovanou za těmito podmínkami.
