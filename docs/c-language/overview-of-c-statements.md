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
ms.openlocfilehash: bfa6840553055202f26f55e1dc5971bfd047b2de
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857070"
---
# <a name="overview-of-c-statements"></a>Přehled příkazů jazyka C

Příkazy C sestávají z tokenů, výrazů a jiných příkazů. Příkaz tvořící součást jiného příkazu je nazýván „tělem“ okolního příkazu. Typy příkazů dané následující syntaxí jsou popsány v tomto oddílu.

## <a name="syntax"></a>Syntaxe

*příkaz*: [označený – příkaz](../c-language/goto-and-labeled-statements-c.md)

[složený příkaz](../c-language/compound-statement-c.md)

[příkaz Expression-](../c-language/expression-statement-c.md)

[Výběr – příkaz](../c-language/if-statement-c.md)

[příkaz iterace](../c-language/do-while-statement-c.md)

[příkaz skoku](../c-language/break-statement-c.md)

[try-except-Statement](../c-language/try-except-statement-c.md) /* specifické pro společnost Microsoft\*/

[try-finally-příkaz](../c-language/try-finally-statement-c.md)  / \* specifický pro společnost Microsoft\*/

Tělem příkazu je často „složený příkaz“. Složený příkaz sestává z jiných příkazů, které mohou obsahovat klíčová slova. Složený příkaz je oddělen složenými závorkami (**{}**). Všechny ostatní příkazy jazyka C končí středníkem (**;**). Středník je zakončením příkazu.

Příkaz Expression obsahuje výraz jazyka C, který může obsahovat aritmetické nebo logické operátory zavedené ve [výrazech a přiřazeních](../c-language/expressions-and-assignments.md). Nulový příkaz je prázdným příkazem.

Všechny příkazy jazyka C mohou začínat identifikačním popiskem sestávajícím z názvu a dvojtečky. Jelikož pouze příkaz `goto` rozpoznává popisky příkazů, jsou tyto popisky popsány spolu s příkazem `goto`. Další informace naleznete v tématu [Příkazy GoTo a labeled](../c-language/goto-and-labeled-statements-c.md) .

## <a name="see-also"></a>Viz také

[Příkazy](../c-language/statements-c.md)
