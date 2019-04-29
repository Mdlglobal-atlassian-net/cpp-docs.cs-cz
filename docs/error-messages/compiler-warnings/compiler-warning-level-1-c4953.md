---
title: Kompilátor upozornění (úroveň 1) C4953
ms.date: 08/27/2018
f1_keywords:
- C4953
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
ms.openlocfilehash: 1948342e1ff97c38ca3a44694dc7e7d399d96825
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384150"
---
# <a name="compiler-warning-level-1-c4953"></a>Kompilátor upozornění (úroveň 1) C4953

> Inlinee "*funkce*' byl upraven od shromáždění dat profilu data profilu se nepoužívá

Při použití [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), kompilátor zjistil vstupní modul, který byl znovu zkompilovat po `/LTCG:PGINSTRUMENT` a má funkci (*funkce*), který byl upraven a kde existující testovací běhy identifikované fungovat jako kandidátem pro vkládání. Ale v důsledku z rekompilace modulu, funkce nebude kandidátem pro vkládání.

Toto upozornění je informační. Pokud chcete vyřešit toto upozornění, spusťte `/LTCG:PGINSTRUMENT`, znovu všech testů běží a spusťte `/LTCG:PGOPTIMIZE`.

Toto upozornění by měl být nahrazen chybu, pokud `/LTCG:PGOPTIMIZE` nepoužilo.