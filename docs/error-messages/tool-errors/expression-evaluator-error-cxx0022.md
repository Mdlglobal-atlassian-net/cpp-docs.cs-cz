---
title: Chyba při vyhodnocování výrazu CXX0022
ms.date: 11/04/2016
f1_keywords:
- CXX0022
helpviewer_keywords:
- CXX0022
- CAN0022
ms.assetid: f6b299ac-a4ee-492c-bd9f-6fff005bc537
ms.openlocfilehash: 5858ce936acfb8b949351c9263f3a9379c73648e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195822"
---
# <a name="expression-evaluator-error-cxx0022"></a>Chyba při vyhodnocování výrazu CXX0022

volání funkce před _main

Vyhodnocovací filtr výrazů jazyka C nemůže vyhodnotit funkci předtím, než ladicí program zadal funkci **_main**. Program není správně inicializován, dokud nebyl volán **_main** .

Tato chyba je shodná s CAN0022.
