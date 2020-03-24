---
title: Upozornění kompilátoru (úroveň 1) C4953
ms.date: 08/27/2018
f1_keywords:
- C4953
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
ms.openlocfilehash: 46f07227b5df62938cc51a7be4cf4f3595a0d947
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174516"
---
# <a name="compiler-warning-level-1-c4953"></a>Upozornění kompilátoru (úroveň 1) C4953

> Inlineing*Function*se od shromáždění dat profilu upravovala. data profilu se nepoužijí.

Při použití [/LTCG: PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)Kompilátor zjistil vstupní modul, který byl znovu zkompilován po `/LTCG:PGINSTRUMENT` a má funkci (*funkci*), která byla upravena a kde existující testovací běhy identifikovaly funkci jako kandidát pro vkládání. V důsledku opětovné kompilace modulu již funkce nebude kandidátem na vkládání.

Toto upozornění je informativní. Chcete-li vyřešit toto upozornění, spusťte `/LTCG:PGINSTRUMENT`, znovu proveďte všechny testovací běhy a spusťte `/LTCG:PGOPTIMIZE`.

Toto upozornění by bylo nahrazeno chybou, pokud byla `/LTCG:PGOPTIMIZE` použita.
