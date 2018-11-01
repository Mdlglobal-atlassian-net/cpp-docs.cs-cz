---
title: Chyba matematické operace M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: d60e9b6284c79828fda1f7af542fcf197f189ad0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451009"
---
# <a name="math-error-m6108"></a>Chyba matematické operace M6108

Druhá odmocnina

Operand v rámci operace druhou odmocninu byla záporná.

Program se ukončí s ukončovacím kódem 136.

> [!NOTE]
>  `sqrt` Funkce knihovny run-time jazyka C a vnitřní funkce až po FORTRAN **SQRT** negenerují k této chybě. C `sqrt` funkce zkontroluje argument před provedením operace a vrací chybovou hodnotu, pokud operand je záporný. FORTRAN **SQRT** funkce generuje chybu domény [operace M6201](../../error-messages/tool-errors/math-error-m6201.md) místo této chyby.