---
title: Vyhodnocování výrazu CXX0024 chyba | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0024
dev_langs:
- C++
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2816be7bb1d33757d9722d605d461ac6fb34fadd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118190"
---
# <a name="expression-evaluator-error-cxx0024"></a>Chyba při vyhodnocování výrazu CXX0024

operace potřebuje l-value

Výraz, který není vyhodnocen na l hodnota zadaná pro operaci, která vyžaduje l hodnotou.

L hodnota (tedy volat, protože se zobrazí na levé straně příkazu přiřazení) je výraz, který odkazuje na umístění v paměti.

Například `buffer[count]` je platný l hodnotou, protože odkazuje na umístění konkrétní paměťové. Logické porovnání `zed != 0` není platnou l hodnotou, protože je vyhodnocen jako TRUE nebo FALSE, ne na adresu paměti.

Tato chyba se shoduje s CAN0024.