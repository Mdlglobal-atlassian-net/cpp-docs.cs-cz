---
title: Chyba při vyhodnocování výrazu CXX0024
ms.date: 11/04/2016
f1_keywords:
- CXX0024
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
ms.openlocfilehash: 93f8389ed3959d5747e46c1234fd8d2eae0f1ae5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359836"
---
# <a name="expression-evaluator-error-cxx0024"></a>Chyba při vyhodnocování výrazu CXX0024

operace potřebuje l-value

Výraz, který není vyhodnocen na l hodnota zadaná pro operaci, která vyžaduje l hodnotou.

L hodnota (tedy volat, protože se zobrazí na levé straně příkazu přiřazení) je výraz, který odkazuje na umístění v paměti.

Například `buffer[count]` je platný l hodnotou, protože odkazuje na umístění konkrétní paměťové. Logické porovnání `zed != 0` není platnou l hodnotou, protože je vyhodnocen jako TRUE nebo FALSE, ne na adresu paměti.

Tato chyba se shoduje s CAN0024.