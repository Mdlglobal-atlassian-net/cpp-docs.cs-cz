---
title: 1.4 dodržování předpisů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 662ad260-b9a1-43b7-b269-ef6ff0714e05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a332d8fb5de172c363c6f9c1bebba65d6fa0ff8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381813"
---
# <a name="14-compliance"></a>1.4 Kompatibilita

Je implementace rozhraní API pro C/C++ OpenMP *CLS OpenMP* pokud rozpozná a zachovává sémantiku ze všech prvků této specifikace, který je uveden v kapitoly 1, 2, 3, 4, a dodatky C. dodatku A, B, D, E a F jsou určené pro informace mají jenom a nejsou součástí specifikace. Implementace, které zahrnují jenom podmnožinu rozhraní API nejsou kompatibilní s OpenMP.

OpenMP – C a C++ API je rozšířením základní jazyk, který podporuje implementaci. Pokud základní jazyk nepodporuje konstrukce jazyka nebo rozšíření, které se zobrazí v tomto dokumentu, implementace OpenMP není vyžadována pro její podporu.

Všechny standardní funkce knihovny C a C++ a předdefinované funkce (to znamená, funkce, které kompilátor nemá specifické znalosti) musí být bezpečné pro vlákna. Nesynchronizované použití těchto funkcí bezpečné pro vlákna v různých vláknech uvnitř paralelní oblasti nevytváří nedefinované chování. Chování však nemusí být stejný jako v sériových oblastech. (Náhodné číslo funkce generování je příklad).

Rozhraní API jazyka C/C++ OpenMP – Určuje, že určité chování *definované implementací.* Vyhovující implementace OpenMP – je potřeba definovat a dokumentovat jeho chování v těchto případech. Zobrazit [příloha E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md), stránce 97 seznam chování definované implementací.