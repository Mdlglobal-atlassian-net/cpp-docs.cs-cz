---
title: Chyba matematické operace M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: c6bd403437ee5e55eaf4add288995d0e4aa76c3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361974"
---
# <a name="math-error-m6108"></a>Chyba matematické operace M6108

Odmocnina

Operand v operaci s druhou odmocninou byl záporný.

Program končí s ukončovacím kódem 136.

> [!NOTE]
> Funkce `sqrt` v knihovně run-time Jazyka C a vnitřní funkce FORTRAN **SQRT** tuto chybu negenerují. Funkce `sqrt` C zkontroluje argument před provedením operace a vrátí chybovou hodnotu, pokud je operand záporný. Funkce FORTRAN **SQRT** generuje chybu domény [M6201](../../error-messages/tool-errors/math-error-m6201.md) namísto této chyby.
