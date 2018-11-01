---
title: Kompilátor upozornění (úroveň 1) C4952
ms.date: 08/27/2018
f1_keywords:
- C4952
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
ms.openlocfilehash: c2e9b88125655d9ea0abe3e65500b149289ba83b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537576"
---
# <a name="compiler-warning-level-1-c4952"></a>Kompilátor upozornění (úroveň 1) C4952

> "*funkce*': nenašla se žádná data profilu v databázi programu"*pgd_file*.

Při použití [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), kompilátor zjistil vstupní modul, který byl znovu zkompilovat po `/LTCG:PGINSTRUMENT` a obsahuje novou funkci (*funkce*) k dispozici.

Toto upozornění je informační. Pokud chcete vyřešit toto upozornění, spusťte `/LTCG:PGINSTRUMENT`, znovu všech testů běží a spusťte `/LTCG:PGOPTIMIZE`.

Toto upozornění by měl být nahrazen chybu, pokud `/LTCG:PGOPTIMIZE` nepoužilo.