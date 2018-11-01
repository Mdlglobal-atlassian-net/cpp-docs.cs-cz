---
title: Chyba při vyhodnocování výrazu CXX0065
ms.date: 11/04/2016
f1_keywords:
- CXX0065
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
ms.openlocfilehash: 7b62e42da2a74d910e2dc56ce2dfcb5cb38f2bfa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571779"
---
# <a name="expression-evaluator-error-cxx0065"></a>Chyba při vyhodnocování výrazu CXX0065

Proměnná musí rámec zásobníku

Výraz obsahuje proměnné, která existuje v aktuálním oboru, ale ještě nebyl vytvořen.

Této chybě může dojít, když jste vkročili prologu funkce ale ještě není nastavení rámce zásobníku pro funkci, nebo pokud jste vkročili ukončovací kód pro funkci.

Krokovat kód prologu, dokud rámce zásobníku je nastavený před vyhodnocením výrazu.

Tato chyba se shoduje s CAN0065.