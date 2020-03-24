---
title: Chyba při vyhodnocování výrazu CXX0024
ms.date: 11/04/2016
f1_keywords:
- CXX0024
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
ms.openlocfilehash: 525210090b0a4c2966f2e1432f85fd4bb6a8156d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195757"
---
# <a name="expression-evaluator-error-cxx0024"></a>Chyba při vyhodnocování výrazu CXX0024

operace potřebuje l-value.

Výraz, který není vyhodnocen jako l-value, byl zadán pro operaci, která vyžaduje l-value.

L-hodnota (tak je volána, protože se zobrazí na levé straně příkazu přiřazení) je výraz, který odkazuje na umístění v paměti.

Například `buffer[count]` je platná l-hodnota, protože odkazuje na konkrétní umístění v paměti. Logické porovnání `zed != 0` není platná l-hodnota, protože je vyhodnocena na hodnotu TRUE nebo FALSE, nikoli na adresu paměti.

Tato chyba je shodná s CAN0024.
