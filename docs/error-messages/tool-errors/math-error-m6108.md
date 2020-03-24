---
title: Chyba matematické operace M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: 68e6ae823613d87eb01c443b564b46746259cd7b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173722"
---
# <a name="math-error-m6108"></a>Chyba matematické operace M6108

Druhá odmocnina

Operand v operaci čtvercového kořene byl záporný.

Program se ukončí s ukončovacím kódem 136.

> [!NOTE]
>  Funkce `sqrt` v knihovně run-time jazyka C a funkce **Sqrt** vnitřních funkcí FORTRAN tuto chybu negeneruje. Funkce `sqrt` jazyka C před provedením operace zkontroluje argument a vrátí chybovou hodnotu, pokud je operand záporný. Funkce FORTRAN **odmocniny** GENERUJE chybu domény [matematické operace M6201](../../error-messages/tool-errors/math-error-m6201.md) namísto této chyby.
