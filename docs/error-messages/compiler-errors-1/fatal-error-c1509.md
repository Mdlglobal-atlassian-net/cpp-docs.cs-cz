---
title: Závažná chyba C1509 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1509
dev_langs:
- C++
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 837ab5b7cf76b724726c6c52fbfe974d4da6ca85
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033131"
---
# <a name="fatal-error-c1509"></a>Závažná chyba C1509

limit kompilátoru: moc velký počet stavů obslužné rutiny výjimek v funkce 'function'. zjednodušení – funkce

Kód překračuje vnitřní limit o stavech obslužné rutiny výjimek (32 768 státy).

Nejčastější příčinou je, že funkce obsahuje složitý výraz uživatelsky definované třídy, proměnné a aritmetické operátory.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Zjednodušte přiřazování běžné podvýrazy k dočasné proměnné výrazů.

1. Funkce rozdělte na menší funkce.