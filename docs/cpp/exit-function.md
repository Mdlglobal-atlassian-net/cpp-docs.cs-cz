---
title: exit – funkce
ms.date: 11/04/2016
f1_keywords:
- Exit
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
ms.openlocfilehash: 82c9d00a49c8a080d893a51052739a0265ad0860
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532558"
---
# <a name="exit-function"></a>exit – funkce

**Ukončit** funkce deklarovaná ve standardním vloženém souboru \<stdlib.h >, ukončuje program jazyka C++.

Hodnota zadaná jako argument **ukončit** je vrácena operačnímu systému jako návratový nebo ukončovací kód programu. Dle konvence návratový kód nula znamená, že byl program dokončen úspěšně.

> [!NOTE]
>  Můžete použít konstanty EXIT_FAILURE a EXIT_SUCCESS definované v \<stdlib.h >, indikující úspěch nebo neúspěch programu.

Vydání **vrátit** příkaz z `main` je ekvivalentní volání funkce **ukončit** funkce s návratovou hodnotou jako svůj argument.

Další informace najdete v tématu [ukončit](../c-runtime-library/reference/exit-exit-exit.md) v *Run-Time Library Reference*.

## <a name="see-also"></a>Viz také:

[Ukončení programu](../cpp/program-termination.md)