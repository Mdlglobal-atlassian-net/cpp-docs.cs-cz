---
title: Chyba při vyhodnocování výrazu CXX0015
ms.date: 11/04/2016
f1_keywords:
- CXX0015
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
ms.openlocfilehash: f73aef18563426d28a81b92b3c37d1b7e345d0d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662043"
---
# <a name="expression-evaluator-error-cxx0015"></a>Chyba při vyhodnocování výrazu CXX0015

výraz je příliš složitý (přetečení zásobníku)

Výraz zadaný byla příliš složité nebo jsou vnořené moc hluboko množství úložiště k dispozici pro vyhodnocování výrazů C.

Přetečení obvykle dochází z důvodu příliš mnoha čekající výpočtů.

Změna uspořádání výraz tak, aby jednotlivé komponenty výraz lze vyhodnotit, jako je došlo k, namísto nutnosti čekání na ostatní části výraz, který má být vypočtena.

Výraz rozdělte do více příkazů.

Tato chyba se shoduje s CAN0015.