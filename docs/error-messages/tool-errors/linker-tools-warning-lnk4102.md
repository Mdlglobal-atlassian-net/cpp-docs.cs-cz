---
title: Upozornění linkerů LNK4102
ms.date: 11/04/2016
f1_keywords:
- LNK4102
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
ms.openlocfilehash: fda1fdb03a7629894f846bb20ed84df519239327
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183303"
---
# <a name="linker-tools-warning-lnk4102"></a>Upozornění linkerů LNK4102

Export odstraňující název destruktoru; Image možná nebude správně fungovat.

Program se pokusil exportovat odstraněný destruktor. Výsledné odstranění může nastat v rámci hranice knihovny DLL tak, že proces může uvolnit paměť, kterou nevlastní. Ujistěte se, že daný symbol není uveden v souboru. def a že symbol není uveden jako argument možnosti **/Import** nebo **/Export** v příkazovém řádku linkeru.

Při opětovném sestavování knihovny run-time jazyka C můžete tuto zprávu ignorovat.
