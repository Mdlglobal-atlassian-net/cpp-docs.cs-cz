---
title: Upozornění kompilátoru (úroveň 3) C4723
ms.date: 11/04/2016
f1_keywords:
- C4723
helpviewer_keywords:
- C4723
ms.assetid: 07669d14-3fd8-4a43-94bc-b61c50e58460
ms.openlocfilehash: 3a47c6f7e83abfc785d602d8ee0734be5d0fa962
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174086"
---
# <a name="compiler-warning-level-3-c4723"></a>Upozornění kompilátoru (úroveň 3) C4723

potenciální dělení nulou

Druhý operand v operaci dělení vyhodnocen jako nula v době kompilace a poskytuje nedefinované výsledky.

Toto upozornění se vydává jenom v případě, že se používá [/og](../../build/reference/og-global-optimizations.md) nebo možnost optimalizace, která implikuje/og.

Kompilátor pravděpodobně vygeneroval nulový operand.
