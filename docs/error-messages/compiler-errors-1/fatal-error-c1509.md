---
title: Závažná chyba C1509
ms.date: 11/04/2016
f1_keywords:
- C1509
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
ms.openlocfilehash: efd5b9dd5cdd7ee174bc786c38d9dd841e2ad6ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620001"
---
# <a name="fatal-error-c1509"></a>Závažná chyba C1509

limit kompilátoru: moc velký počet stavů obslužné rutiny výjimek v funkce 'function'. zjednodušení – funkce

Kód překračuje vnitřní limit o stavech obslužné rutiny výjimek (32 768 státy).

Nejčastější příčinou je, že funkce obsahuje složitý výraz uživatelsky definované třídy, proměnné a aritmetické operátory.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Zjednodušte přiřazování běžné podvýrazy k dočasné proměnné výrazů.

1. Funkce rozdělte na menší funkce.