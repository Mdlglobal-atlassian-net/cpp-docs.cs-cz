---
title: Přehled příkazů jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- semicolon, in C statements
- statements, C
- semicolon
- statements, about statements
- Visual C, statements
ms.assetid: 0d49837a-5399-4881-b60c-af5f4e9720de
ms.openlocfilehash: 906beb7c5c2edfc448daadb1f4c5a111f7877b91
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613717"
---
# <a name="overview-of-c-statements"></a>Přehled příkazů jazyka C

Příkazy C sestávají z tokenů, výrazů a jiných příkazů. Příkaz tvořící součást jiného příkazu je nazýván „tělem“ okolního příkazu. Typy příkazů dané následující syntaxí jsou popsány v tomto oddílu.

## <a name="syntax"></a>Syntaxe

*příkaz*: [příkaz s popiskem](../c-language/goto-and-labeled-statements-c.md)

[compound-statement](../c-language/compound-statement-c.md)

[příkaz výrazu](../c-language/expression-statement-c.md)

[příkaz výběru](../c-language/if-statement-c.md)

[iterace – příkaz](../c-language/do-while-statement-c.md)

[příkaz-skoku](../c-language/break-statement-c.md)

[s výjimkou příkazu Try](../c-language/try-except-statement-c.md)

/ * Specifické pro Microsoft \* / [try-finally-statement](../c-language/try-finally-statement-c.md)  / \* specifické pro Microsoft \*/

Tělem příkazu je často „složený příkaz“. Složený příkaz sestává z jiných příkazů, které mohou obsahovat klíčová slova. Složený příkaz je oddělen složenými závorkami (**{}**). Všechny ostatní příkazy jazyka C končí středníkem (**;**). Středník je zakončením příkazu.

Příkaz výrazu obsahuje výraz jazyka C, který může obsahovat aritmetické nebo logické operátory představené v [výrazy a přiřazení](../c-language/expressions-and-assignments.md). Nulový příkaz je prázdným příkazem.

Všechny příkazy jazyka C mohou začínat identifikačním popiskem sestávajícím z názvu a dvojtečky. Jelikož pouze příkaz `goto` rozpoznává popisky příkazů, jsou tyto popisky popsány spolu s příkazem `goto`. Zobrazit [příkaz goto a příkazy s popiskem](../c-language/goto-and-labeled-statements-c.md) Další informace.

## <a name="see-also"></a>Viz také

[Příkazy](../c-language/statements-c.md)